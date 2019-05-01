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
ms.openlocfilehash: a59ff4c956724c614342f0ee4c0622a67f1c25e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054952"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="cb70e-102">Is – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb70e-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="cb70e-103">Porovná dvě proměnné objektových referencí.</span><span class="sxs-lookup"><span data-stu-id="cb70e-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb70e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb70e-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="cb70e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="cb70e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="cb70e-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="cb70e-106">Required.</span></span> <span data-ttu-id="cb70e-107">Žádné `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cb70e-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="cb70e-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="cb70e-108">Required.</span></span> <span data-ttu-id="cb70e-109">Žádné `Object` název.</span><span class="sxs-lookup"><span data-stu-id="cb70e-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="cb70e-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="cb70e-110">Required.</span></span> <span data-ttu-id="cb70e-111">Žádné `Object` název.</span><span class="sxs-lookup"><span data-stu-id="cb70e-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb70e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb70e-112">Remarks</span></span>  
 <span data-ttu-id="cb70e-113">`Is` Určuje operátor, pokud dva odkazy na objekty odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="cb70e-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="cb70e-114">Neprovádí však porovnání hodnot.</span><span class="sxs-lookup"><span data-stu-id="cb70e-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="cb70e-115">Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="cb70e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="cb70e-116">`Is` Můžete také použít s `TypeOf` – klíčové slovo, aby `TypeOf`... `Is` výraz, který testuje, jestli je kompatibilní s datovým typem proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="cb70e-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb70e-117">`Is` – Klíčové slovo se používá také v [vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cb70e-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb70e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb70e-118">Example</span></span>  
 <span data-ttu-id="cb70e-119">V následujícím příkladu `Is` operátor porovnání dvojice odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="cb70e-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="cb70e-120">Výsledky jsou přiřazeny k `Boolean` hodnotu udávající, zda dva objekty jsou identické.</span><span class="sxs-lookup"><span data-stu-id="cb70e-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="cb70e-121">Jak ukazuje předchozí příklad, můžete použít `Is` operátor testování obou časné a pozdní vazby objektů.</span><span class="sxs-lookup"><span data-stu-id="cb70e-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb70e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb70e-122">See also</span></span>

- [<span data-ttu-id="cb70e-123">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="cb70e-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="cb70e-124">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="cb70e-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="cb70e-125">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb70e-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="cb70e-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb70e-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="cb70e-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="cb70e-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cb70e-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="cb70e-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
