---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a><span data-ttu-id="8bd98-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd98-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="8bd98-103">Určuje, že je předán argument tak, že volané procedury nebo vlastnost nelze změnit hodnotu proměnné základní argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="8bd98-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd98-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bd98-104">Remarks</span></span>  
 <span data-ttu-id="8bd98-105">`ByVal` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="8bd98-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8bd98-106">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="8bd98-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="8bd98-107">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="8bd98-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8bd98-108">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="8bd98-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="8bd98-109">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="8bd98-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8bd98-110">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="8bd98-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="8bd98-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bd98-111">Example</span></span>  
 <span data-ttu-id="8bd98-112">Následující příklad ukazuje použití `ByVal` předávání mechanismus s argumentem odkaz na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="8bd98-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="8bd98-113">V příkladu je argument `c1`, instance třídy `Class1`.</span><span class="sxs-lookup"><span data-stu-id="8bd98-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="8bd98-114">`ByVal`kód v postupech nebude změna základní hodnota argumentu odkaz, `c1`, ale nechrání přístupné pole a vlastnosti `c1`.</span><span class="sxs-lookup"><span data-stu-id="8bd98-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8bd98-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bd98-115">See Also</span></span>  
 [<span data-ttu-id="8bd98-116">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8bd98-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="8bd98-117">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="8bd98-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
