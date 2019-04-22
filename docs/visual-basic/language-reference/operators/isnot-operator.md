---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: e07a775eec003a3e488f6909181aed3f742b4b91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833513"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="1c590-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c590-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="1c590-103">Porovná dvě proměnné objektových referencí.</span><span class="sxs-lookup"><span data-stu-id="1c590-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c590-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c590-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="1c590-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1c590-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1c590-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c590-106">Required.</span></span> <span data-ttu-id="1c590-107">A `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c590-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="1c590-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c590-108">Required.</span></span> <span data-ttu-id="1c590-109">Žádné `Object` proměnné nebo výrazu.</span><span class="sxs-lookup"><span data-stu-id="1c590-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="1c590-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c590-110">Required.</span></span> <span data-ttu-id="1c590-111">Žádné `Object` proměnné nebo výrazu.</span><span class="sxs-lookup"><span data-stu-id="1c590-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c590-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c590-112">Remarks</span></span>  
 <span data-ttu-id="1c590-113">`IsNot` Určuje operátor, pokud reference na dva objekty odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="1c590-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="1c590-114">Neprovádí však porovnání hodnot.</span><span class="sxs-lookup"><span data-stu-id="1c590-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="1c590-115">Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="1c590-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="1c590-116">`IsNot` je opakem `Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="1c590-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="1c590-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodnou syntaxe `Not` a `Is`, což může být obtížně čitelné.</span><span class="sxs-lookup"><span data-stu-id="1c590-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="1c590-118">Můžete použít `Is` a `IsNot` operátory k otestování objekty časné vazby a s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="1c590-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c590-119">`IsNot` Operátor nelze použít k porovnání výrazy vrácených `TypeOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="1c590-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="1c590-120">Místo toho je nutné použít `Not` a `Is` operátory.</span><span class="sxs-lookup"><span data-stu-id="1c590-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c590-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c590-121">Example</span></span>  
 <span data-ttu-id="1c590-122">Následující příklad kódu používá obě `Is` operátor a `IsNot` operátor k dosažení stejného porovnání.</span><span class="sxs-lookup"><span data-stu-id="1c590-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="1c590-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c590-123">See also</span></span>

- [<span data-ttu-id="1c590-124">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="1c590-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="1c590-125">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="1c590-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="1c590-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c590-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1c590-127">Postupy: Otestujte, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="1c590-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
