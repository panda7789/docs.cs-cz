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
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666850"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="98eff-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98eff-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="98eff-103">Určuje, že argument je předán [hodnotou](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), takže volaná procedura nebo vlastnost nemůže změnit hodnotu proměnné podkladové hodnoty argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="98eff-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="98eff-104">Pokud není zadán žádný modifikátor, je jako výchozí použita hodnota ByVal.</span><span class="sxs-lookup"><span data-stu-id="98eff-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="98eff-105">Vzhledem k tomu, že je výchozí hodnota, není nutné explicitně zadat `ByVal` klíčové slovo v podpisech metody.</span><span class="sxs-lookup"><span data-stu-id="98eff-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="98eff-106">Je v úmyslu způsobit vysokou úroveň kódu a často vede k přehlédnutí na jiné `ByRef` než výchozí klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="98eff-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="98eff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98eff-107">Remarks</span></span>
 <span data-ttu-id="98eff-108">V těchto kontextech lze použít Modifikátor:`ByVal`</span><span class="sxs-lookup"><span data-stu-id="98eff-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="98eff-109">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="98eff-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

 [<span data-ttu-id="98eff-110">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="98eff-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [<span data-ttu-id="98eff-111">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="98eff-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [<span data-ttu-id="98eff-112">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="98eff-112">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [<span data-ttu-id="98eff-113">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="98eff-113">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="98eff-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="98eff-114">Example</span></span>
 <span data-ttu-id="98eff-115">Následující příklad ukazuje použití `ByVal` mechanismu předávání parametrů s argumentem typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="98eff-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="98eff-116">V příkladu je `c1`argumentem instance třídy `Class1`.</span><span class="sxs-lookup"><span data-stu-id="98eff-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="98eff-117">`ByVal`zabraňuje kódu v postupech v změně podkladové hodnoty argumentu `c1`odkazu,,, ale nechrání dostupná pole a `c1`vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98eff-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="98eff-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98eff-118">See also</span></span>

- [<span data-ttu-id="98eff-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="98eff-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="98eff-120">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="98eff-120">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
