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
ms.openlocfilehash: 076289ff303dce58f036d6c7cb1505b151da19f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602980"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="fce18-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fce18-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="fce18-103">Určuje, že je předán argument tak, že volané procedury nebo vlastnost nelze změnit hodnotu proměnné základní argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="fce18-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fce18-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fce18-104">Remarks</span></span>  
 <span data-ttu-id="fce18-105">`ByVal` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="fce18-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="fce18-106">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="fce18-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="fce18-107">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="fce18-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="fce18-108">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="fce18-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="fce18-109">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="fce18-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="fce18-110">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="fce18-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="fce18-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="fce18-111">Example</span></span>  
 <span data-ttu-id="fce18-112">Následující příklad ukazuje použití `ByVal` předávání mechanismus s argumentem odkaz na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="fce18-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="fce18-113">V příkladu je argument `c1`, instance třídy `Class1`.</span><span class="sxs-lookup"><span data-stu-id="fce18-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="fce18-114">`ByVal` kód v postupech nebude změna základní hodnota argumentu odkaz, `c1`, ale nechrání přístupné pole a vlastnosti `c1`.</span><span class="sxs-lookup"><span data-stu-id="fce18-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fce18-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fce18-115">See Also</span></span>  
 [<span data-ttu-id="fce18-116">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fce18-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="fce18-117">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="fce18-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
