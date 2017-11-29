---
title: "Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="74277-102">Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="74277-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="74277-103">Můžete použít `Function` postup vrátit hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="74277-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="74277-104">K vytvoření procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="74277-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="74277-105">Mimo jiné postup použijte `Function` prohlášení, za nímž následuje `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="74277-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="74277-106">V `Function` prohlášení, postupujte podle `Function` – klíčové slovo s názvem postupu a seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="74277-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="74277-107">Postupujte podle závorkách s `As` klauzule zadat datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="74277-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="74277-108">Umístit postup kód příkazy mezi `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="74277-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="74277-109">Použití `Return` příkaz k vrácení hodnoty volání kódu.</span><span class="sxs-lookup"><span data-stu-id="74277-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="74277-110">Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="74277-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="74277-111">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="74277-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="74277-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="74277-112">See Also</span></span>  
 [<span data-ttu-id="74277-113">Postupy</span><span class="sxs-lookup"><span data-stu-id="74277-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="74277-114">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="74277-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="74277-115">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="74277-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="74277-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="74277-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="74277-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="74277-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="74277-118">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="74277-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="74277-119">Postupy: vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="74277-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="74277-120">Postupy: volání procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="74277-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
