---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: c4cdafafa6bae3246c0512e28f94fde7e88d230b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373021"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="b0be5-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0be5-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="b0be5-103">Určuje, že argument je předán [hodnotou](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), takže volaná procedura nebo vlastnost nemůže změnit hodnotu proměnné podkladové hodnoty argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b0be5-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="b0be5-104">Pokud není zadán žádný modifikátor, je jako výchozí použita hodnota ByVal.</span><span class="sxs-lookup"><span data-stu-id="b0be5-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="b0be5-105">Vzhledem k tomu, že je výchozí hodnota, není nutné explicitně zadat `ByVal` klíčové slovo v podpisech metody.</span><span class="sxs-lookup"><span data-stu-id="b0be5-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="b0be5-106">Je v úmyslu způsobit vysokou úroveň kódu a často vede k přehlédnutí na jiné než výchozí `ByRef` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b0be5-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0be5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0be5-107">Remarks</span></span>
 <span data-ttu-id="b0be5-108">`ByVal`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="b0be5-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="b0be5-109">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0be5-109">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="b0be5-110">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0be5-110">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="b0be5-111">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0be5-111">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="b0be5-112">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0be5-112">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="b0be5-113">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0be5-113">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="b0be5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0be5-114">Example</span></span>
 <span data-ttu-id="b0be5-115">Následující příklad ukazuje použití `ByVal` mechanismu předávání parametrů s argumentem typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="b0be5-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="b0be5-116">V příkladu je argumentem `c1` instance třídy `Class1` .</span><span class="sxs-lookup"><span data-stu-id="b0be5-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="b0be5-117">`ByVal`zabraňuje kódu v postupech v změně podkladové hodnoty argumentu odkazu, `c1` ,, ale nechrání dostupná pole a vlastnosti `c1` .</span><span class="sxs-lookup"><span data-stu-id="b0be5-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="b0be5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0be5-118">See also</span></span>

- [<span data-ttu-id="b0be5-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b0be5-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="b0be5-120">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="b0be5-120">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
