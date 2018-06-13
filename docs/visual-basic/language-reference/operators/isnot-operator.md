---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603311"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="1bc10-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bc10-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="1bc10-103">Porovná dvě proměnné objektových referencí.</span><span class="sxs-lookup"><span data-stu-id="1bc10-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bc10-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="1bc10-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1bc10-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1bc10-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1bc10-106">Required.</span></span> <span data-ttu-id="1bc10-107">A `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1bc10-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="1bc10-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1bc10-108">Required.</span></span> <span data-ttu-id="1bc10-109">Všechny `Object` proměnnou nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="1bc10-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="1bc10-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1bc10-110">Required.</span></span> <span data-ttu-id="1bc10-111">Všechny `Object` proměnnou nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="1bc10-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bc10-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bc10-112">Remarks</span></span>  
 <span data-ttu-id="1bc10-113">`IsNot` Operátor určuje, pokud dva odkazy na objekty odkazovat na jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="1bc10-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="1bc10-114">Neprovede však porovnání hodnot.</span><span class="sxs-lookup"><span data-stu-id="1bc10-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="1bc10-115">Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="1bc10-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="1bc10-116">`IsNot` maska je opakem `Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="1bc10-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="1bc10-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodných syntaxi společně s `Not` a `Is`, což může být obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="1bc10-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="1bc10-118">Můžete použít `Is` a `IsNot` operátory k testování objekty časné vazby a pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="1bc10-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bc10-119">`IsNot` Operátor nelze použít k porovnání vrácená z výrazů `TypeOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="1bc10-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="1bc10-120">Místo toho musíte použít `Not` a `Is` operátory.</span><span class="sxs-lookup"><span data-stu-id="1bc10-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc10-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bc10-121">Example</span></span>  
 <span data-ttu-id="1bc10-122">Následující příklad kódu používá i `Is` operátor a `IsNot` operátor provedete stejné porovnání.</span><span class="sxs-lookup"><span data-stu-id="1bc10-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1bc10-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bc10-123">See Also</span></span>  
 [<span data-ttu-id="1bc10-124">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="1bc10-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="1bc10-125">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="1bc10-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="1bc10-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bc10-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1bc10-127">Postupy: Test, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="1bc10-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
