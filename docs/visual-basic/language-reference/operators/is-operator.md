---
title: "Is – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="46795-102">Is – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46795-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="46795-103">Porovná dvě proměnné objektových referencí.</span><span class="sxs-lookup"><span data-stu-id="46795-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46795-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46795-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="46795-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="46795-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="46795-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="46795-106">Required.</span></span> <span data-ttu-id="46795-107">Všechny `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="46795-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="46795-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="46795-108">Required.</span></span> <span data-ttu-id="46795-109">Všechny `Object` název.</span><span class="sxs-lookup"><span data-stu-id="46795-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="46795-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="46795-110">Required.</span></span> <span data-ttu-id="46795-111">Všechny `Object` název.</span><span class="sxs-lookup"><span data-stu-id="46795-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46795-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46795-112">Remarks</span></span>  
 <span data-ttu-id="46795-113">`Is` Operátor určuje, pokud dva odkazy na objekty odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="46795-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="46795-114">Neprovede však porovnání hodnot.</span><span class="sxs-lookup"><span data-stu-id="46795-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="46795-115">Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="46795-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="46795-116">`Is`Můžete také použít s `TypeOf` – klíčové slovo, aby `TypeOf`... `Is` výraz, který testuje, zda je kompatibilní s datovým typem proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="46795-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46795-117">`Is` – Klíčové slovo je používán také [vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="46795-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46795-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="46795-118">Example</span></span>  
 <span data-ttu-id="46795-119">Následující příklad používá `Is` operátor k porovnání páry odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="46795-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="46795-120">Výsledky jsou přiřazeny k `Boolean` hodnotu udávající, zda dva objekty jsou identické.</span><span class="sxs-lookup"><span data-stu-id="46795-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="46795-121">Jak ukazuje předchozí příklad, můžete použít `Is` operátor k testování obě časné a pozdní vazba objekty.</span><span class="sxs-lookup"><span data-stu-id="46795-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46795-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="46795-122">See Also</span></span>  
 [<span data-ttu-id="46795-123">Typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="46795-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="46795-124">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="46795-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="46795-125">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46795-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="46795-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46795-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="46795-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="46795-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="46795-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="46795-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
