---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 5e534eac2300327d4c54c5ce93d8b2c6c538e794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801663"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="d56d8-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56d8-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="d56d8-103">Určuje, že argument se předává takovým způsobem, že volaná procedura nebo vlastnost nelze změnit hodnotu proměnné základní argumentu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d56d8-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d56d8-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d56d8-104">Remarks</span></span>  
 <span data-ttu-id="d56d8-105">`ByVal` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="d56d8-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d56d8-106">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="d56d8-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="d56d8-107">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="d56d8-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d56d8-108">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="d56d8-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="d56d8-109">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="d56d8-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d56d8-110">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="d56d8-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="d56d8-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d56d8-111">Example</span></span>  
 <span data-ttu-id="d56d8-112">Následující příklad ukazuje použití `ByVal` předávání mechanismus s argumentem reference typu parametru.</span><span class="sxs-lookup"><span data-stu-id="d56d8-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="d56d8-113">V tomto příkladu je argument `c1`, instance třídy `Class1`.</span><span class="sxs-lookup"><span data-stu-id="d56d8-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="d56d8-114">`ByVal` zabrání změně podkladovou hodnotu argument odkazu kód v postupech `c1`, ale nechrání dostupná pole a vlastnosti `c1`.</span><span class="sxs-lookup"><span data-stu-id="d56d8-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="d56d8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d56d8-115">See also</span></span>

- [<span data-ttu-id="d56d8-116">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d56d8-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="d56d8-117">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="d56d8-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
