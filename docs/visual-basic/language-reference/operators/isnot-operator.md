---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ffafff915af8a94e9bc135246064e4c049d41838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596459"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="0318c-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0318c-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="0318c-103">Porovná dvě proměnné objektových referencí.</span><span class="sxs-lookup"><span data-stu-id="0318c-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0318c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0318c-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="0318c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0318c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0318c-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0318c-106">Required.</span></span> <span data-ttu-id="0318c-107">A `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0318c-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="0318c-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0318c-108">Required.</span></span> <span data-ttu-id="0318c-109">Žádné `Object` proměnné nebo výrazu.</span><span class="sxs-lookup"><span data-stu-id="0318c-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="0318c-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0318c-110">Required.</span></span> <span data-ttu-id="0318c-111">Žádné `Object` proměnné nebo výrazu.</span><span class="sxs-lookup"><span data-stu-id="0318c-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0318c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0318c-112">Remarks</span></span>  
 <span data-ttu-id="0318c-113">`IsNot` Určuje operátor, pokud reference na dva objekty odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="0318c-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="0318c-114">Neprovádí však porovnání hodnot.</span><span class="sxs-lookup"><span data-stu-id="0318c-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="0318c-115">Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="0318c-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="0318c-116">`IsNot` je opakem `Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="0318c-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="0318c-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodnou syntaxe `Not` a `Is`, což může být obtížně čitelné.</span><span class="sxs-lookup"><span data-stu-id="0318c-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="0318c-118">Můžete použít `Is` a `IsNot` operátory k otestování objekty časné vazby a s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="0318c-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0318c-119">`IsNot` Operátor nelze použít k porovnání výrazy vrácených `TypeOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="0318c-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="0318c-120">Místo toho je nutné použít `Not` a `Is` operátory.</span><span class="sxs-lookup"><span data-stu-id="0318c-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0318c-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="0318c-121">Example</span></span>  
 <span data-ttu-id="0318c-122">Následující příklad kódu používá obě `Is` operátor a `IsNot` operátor k dosažení stejného porovnání.</span><span class="sxs-lookup"><span data-stu-id="0318c-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0318c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0318c-123">See also</span></span>
- [<span data-ttu-id="0318c-124">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="0318c-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0318c-125">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="0318c-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="0318c-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0318c-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0318c-127">Postupy: Otestujte, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="0318c-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
