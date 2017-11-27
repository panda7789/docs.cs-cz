---
title: "IsNot – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isnot
helpviewer_keywords: IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="2f53e-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f53e-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="2f53e-103">Porovná dvě proměnné objektových referencí.</span><span class="sxs-lookup"><span data-stu-id="2f53e-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f53e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f53e-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="2f53e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2f53e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="2f53e-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2f53e-106">Required.</span></span> <span data-ttu-id="2f53e-107">A `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2f53e-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="2f53e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2f53e-108">Required.</span></span> <span data-ttu-id="2f53e-109">Všechny `Object` proměnnou nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="2f53e-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="2f53e-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2f53e-110">Required.</span></span> <span data-ttu-id="2f53e-111">Všechny `Object` proměnnou nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="2f53e-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f53e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f53e-112">Remarks</span></span>  
 <span data-ttu-id="2f53e-113">`IsNot` Operátor určuje, pokud dva odkazy na objekty odkazovat na jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="2f53e-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="2f53e-114">Neprovede však porovnání hodnot.</span><span class="sxs-lookup"><span data-stu-id="2f53e-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="2f53e-115">Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="2f53e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="2f53e-116">`IsNot`maska je opakem `Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="2f53e-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="2f53e-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodných syntaxi společně s `Not` a `Is`, což může být obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="2f53e-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="2f53e-118">Můžete použít `Is` a `IsNot` operátory k testování objekty časné vazby a pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2f53e-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f53e-119">`IsNot` Operátor nelze použít k porovnání vrácená z výrazů `TypeOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="2f53e-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="2f53e-120">Místo toho musíte použít `Not` a `Is` operátory.</span><span class="sxs-lookup"><span data-stu-id="2f53e-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f53e-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f53e-121">Example</span></span>  
 <span data-ttu-id="2f53e-122">Následující příklad kódu používá i `Is` operátor a `IsNot` operátor provedete stejné porovnání.</span><span class="sxs-lookup"><span data-stu-id="2f53e-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2f53e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f53e-123">See Also</span></span>  
 [<span data-ttu-id="2f53e-124">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="2f53e-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="2f53e-125">Typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="2f53e-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="2f53e-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f53e-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="2f53e-127">Postupy: Test, zda dva objekty jsou stejné</span><span class="sxs-lookup"><span data-stu-id="2f53e-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
