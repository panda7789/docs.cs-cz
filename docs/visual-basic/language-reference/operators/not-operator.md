---
title: Not – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348298"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="a0b7f-102">Not – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0b7f-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="a0b7f-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0b7f-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a0b7f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a0b7f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a0b7f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-106">Required.</span></span> <span data-ttu-id="a0b7f-107">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="a0b7f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-108">Required.</span></span> <span data-ttu-id="a0b7f-109">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0b7f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0b7f-110">Remarks</span></span>  
 <span data-ttu-id="a0b7f-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a0b7f-112">If `expression` is</span><span class="sxs-lookup"><span data-stu-id="a0b7f-112">If `expression` is</span></span>|<span data-ttu-id="a0b7f-113">The value of `result` is</span><span class="sxs-lookup"><span data-stu-id="a0b7f-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="a0b7f-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a0b7f-115">If bit in `expression` is</span><span class="sxs-lookup"><span data-stu-id="a0b7f-115">If bit in `expression` is</span></span>|<span data-ttu-id="a0b7f-116">The bit in `result` is</span><span class="sxs-lookup"><span data-stu-id="a0b7f-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="a0b7f-117">1</span><span class="sxs-lookup"><span data-stu-id="a0b7f-117">1</span></span>|<span data-ttu-id="a0b7f-118">0</span><span class="sxs-lookup"><span data-stu-id="a0b7f-118">0</span></span>|  
|<span data-ttu-id="a0b7f-119">0</span><span class="sxs-lookup"><span data-stu-id="a0b7f-119">0</span></span>|<span data-ttu-id="a0b7f-120">1</span><span class="sxs-lookup"><span data-stu-id="a0b7f-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a0b7f-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a0b7f-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a0b7f-122">Data Types</span></span>  
 <span data-ttu-id="a0b7f-123">For a Boolean negation, the data type of the result is `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a0b7f-124">For a bitwise negation, the result data type is the same as that of `expression`.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="a0b7f-125">However, if expression is `Decimal`, the result is `Long`.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a0b7f-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="a0b7f-126">Overloading</span></span>  
 <span data-ttu-id="a0b7f-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="a0b7f-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a0b7f-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a0b7f-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b7f-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0b7f-130">Example</span></span>  
 <span data-ttu-id="a0b7f-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="a0b7f-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="a0b7f-133">The preceding example produces results of `False` and `True`, respectively.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b7f-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0b7f-134">Example</span></span>  
 <span data-ttu-id="a0b7f-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="a0b7f-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="a0b7f-137">The preceding example produces results of –11, –9, and –7, respectively.</span><span class="sxs-lookup"><span data-stu-id="a0b7f-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b7f-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0b7f-138">See also</span></span>

- [<span data-ttu-id="a0b7f-139">Logical/Bitwise Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0b7f-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="a0b7f-140">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0b7f-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a0b7f-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="a0b7f-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a0b7f-142">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0b7f-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
