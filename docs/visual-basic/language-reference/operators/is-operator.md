---
title: Is – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349537"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="400e7-102">Is – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="400e7-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="400e7-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="400e7-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="400e7-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="400e7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="400e7-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="400e7-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="400e7-106">Required.</span></span> <span data-ttu-id="400e7-107">Jakákoli `Boolean` hodnota.</span><span class="sxs-lookup"><span data-stu-id="400e7-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="400e7-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="400e7-108">Required.</span></span> <span data-ttu-id="400e7-109">Libovolný `Object` název.</span><span class="sxs-lookup"><span data-stu-id="400e7-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="400e7-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="400e7-110">Required.</span></span> <span data-ttu-id="400e7-111">Libovolný `Object` název.</span><span class="sxs-lookup"><span data-stu-id="400e7-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="400e7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="400e7-112">Remarks</span></span>  
 <span data-ttu-id="400e7-113">Operátor `Is` určuje, zda dva odkazy na objekt odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="400e7-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="400e7-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="400e7-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="400e7-115">Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="400e7-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="400e7-116">`Is` lze také použít s klíčovým slovem `TypeOf` k vytvoření výrazu `TypeOf`...`Is`, který testuje, zda je objektová proměnná kompatibilní s datovým typem.</span><span class="sxs-lookup"><span data-stu-id="400e7-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="400e7-117">Klíčové slovo `Is` se používá také v rámci [výběru... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="400e7-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="400e7-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="400e7-118">Example</span></span>  
 <span data-ttu-id="400e7-119">Následující příklad používá operátor `Is` pro porovnání párů odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="400e7-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="400e7-120">Výsledky jsou přiřazeny `Boolean` hodnotě, která představuje, zda jsou dva objekty identické.</span><span class="sxs-lookup"><span data-stu-id="400e7-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="400e7-121">Jak ukazuje předchozí příklad, lze použít operátor `Is` k otestování počátečních a pozdních vázaných objektů.</span><span class="sxs-lookup"><span data-stu-id="400e7-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400e7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="400e7-122">See also</span></span>

- [<span data-ttu-id="400e7-123">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="400e7-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="400e7-124">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="400e7-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="400e7-125">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="400e7-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="400e7-126">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="400e7-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="400e7-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="400e7-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="400e7-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="400e7-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
