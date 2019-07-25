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
ms.openlocfilehash: abfe1489cb7e0d06b03c308e0704ce6f69ee55da
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433805"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="ea7bc-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea7bc-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="ea7bc-103">Určuje, že argument je předán [hodnotou](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), takže volaná procedura nebo vlastnost nemůže změnit hodnotu proměnné podkladové hodnoty argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ea7bc-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="ea7bc-104">Pokud není zadán žádný modifikátor, je jako výchozí použita hodnota ByVal.</span><span class="sxs-lookup"><span data-stu-id="ea7bc-104">If no modifier is specified, ByVal is the default.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="ea7bc-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea7bc-105">Remarks</span></span>  
 <span data-ttu-id="ea7bc-106">V těchto kontextech lze použít Modifikátor:`ByVal`</span><span class="sxs-lookup"><span data-stu-id="ea7bc-106">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ea7bc-107">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="ea7bc-107">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ea7bc-108">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="ea7bc-108">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ea7bc-109">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="ea7bc-109">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="ea7bc-110">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="ea7bc-110">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ea7bc-111">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="ea7bc-111">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="ea7bc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea7bc-112">Example</span></span>  
 <span data-ttu-id="ea7bc-113">Následující příklad ukazuje použití `ByVal` mechanismu předávání parametrů s argumentem typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="ea7bc-113">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="ea7bc-114">V příkladu je `c1`argumentem instance třídy `Class1`.</span><span class="sxs-lookup"><span data-stu-id="ea7bc-114">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="ea7bc-115">`ByVal`zabraňuje kódu v postupech v změně podkladové hodnoty argumentu `c1`odkazu,,, ale nechrání dostupná pole a `c1`vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea7bc-115">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="ea7bc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea7bc-116">See also</span></span>

- [<span data-ttu-id="ea7bc-117">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ea7bc-117">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="ea7bc-118">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="ea7bc-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
