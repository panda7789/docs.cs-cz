---
title: Is – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 0351d224d9bf08a8f3ca74090de7b9c51c2c61bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701369"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="bba3a-102">Is – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bba3a-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="bba3a-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="bba3a-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bba3a-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="bba3a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bba3a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="bba3a-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bba3a-106">Required.</span></span> <span data-ttu-id="bba3a-107">Jakákoli hodnota `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="bba3a-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="bba3a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bba3a-108">Required.</span></span> <span data-ttu-id="bba3a-109">Libovolný název `Object`.</span><span class="sxs-lookup"><span data-stu-id="bba3a-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="bba3a-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bba3a-110">Required.</span></span> <span data-ttu-id="bba3a-111">Libovolný název `Object`.</span><span class="sxs-lookup"><span data-stu-id="bba3a-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bba3a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bba3a-112">Remarks</span></span>  
 <span data-ttu-id="bba3a-113">Operátor `Is` určuje, zda dva odkazy na objekt odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="bba3a-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="bba3a-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="bba3a-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="bba3a-115">Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="bba3a-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="bba3a-116">`Is` lze také použít s klíčovým slovem `TypeOf` k vytvoření výrazu `TypeOf`... `Is`, který testuje, zda je objektová proměnná kompatibilní s datovým typem.</span><span class="sxs-lookup"><span data-stu-id="bba3a-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bba3a-117">Klíčové slovo `Is` se používá také v rámci [výběru... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bba3a-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba3a-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="bba3a-118">Example</span></span>  
 <span data-ttu-id="bba3a-119">V následujícím příkladu je použit operátor `Is` pro porovnání párů odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="bba3a-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="bba3a-120">Výsledky jsou přiřazeny k hodnotě @no__t 0, která představuje, zda jsou dva objekty identické.</span><span class="sxs-lookup"><span data-stu-id="bba3a-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="bba3a-121">Jak ukazuje předchozí příklad, můžete použít operátor `Is` k otestování počátečních a pozdních vázaných objektů.</span><span class="sxs-lookup"><span data-stu-id="bba3a-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba3a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bba3a-122">See also</span></span>

- [<span data-ttu-id="bba3a-123">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="bba3a-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="bba3a-124">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="bba3a-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="bba3a-125">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bba3a-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="bba3a-126">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bba3a-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bba3a-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="bba3a-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="bba3a-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="bba3a-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
