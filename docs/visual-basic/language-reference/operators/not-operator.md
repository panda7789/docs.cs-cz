---
title: Not – operátor (Visual Basic)
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
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824198"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="23554-102">Not – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23554-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="23554-103">Provede logickou negaci `Boolean` výrazu nebo bitovou negaci numerického výrazu.</span><span class="sxs-lookup"><span data-stu-id="23554-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23554-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23554-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="23554-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="23554-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="23554-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="23554-106">Required.</span></span> <span data-ttu-id="23554-107">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="23554-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="23554-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="23554-108">Required.</span></span> <span data-ttu-id="23554-109">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="23554-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23554-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23554-110">Remarks</span></span>  
 <span data-ttu-id="23554-111">Pro `Boolean` výrazy, následující tabulka ukazuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="23554-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="23554-112">Pokud `expression` je</span><span class="sxs-lookup"><span data-stu-id="23554-112">If `expression` is</span></span>|<span data-ttu-id="23554-113">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="23554-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="23554-114">Pro numerických výrazů `Not` operátor Invertuje bitové hodnoty jakýkoli číselný výraz a nastaví odpovídající bit v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="23554-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="23554-115">Pokud bit v `expression` je</span><span class="sxs-lookup"><span data-stu-id="23554-115">If bit in `expression` is</span></span>|<span data-ttu-id="23554-116">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="23554-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="23554-117">1</span><span class="sxs-lookup"><span data-stu-id="23554-117">1</span></span>|<span data-ttu-id="23554-118">0</span><span class="sxs-lookup"><span data-stu-id="23554-118">0</span></span>|  
|<span data-ttu-id="23554-119">0</span><span class="sxs-lookup"><span data-stu-id="23554-119">0</span></span>|<span data-ttu-id="23554-120">1</span><span class="sxs-lookup"><span data-stu-id="23554-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="23554-121">Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách zajistit správné spuštění.</span><span class="sxs-lookup"><span data-stu-id="23554-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="23554-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="23554-122">Data Types</span></span>  
 <span data-ttu-id="23554-123">Logická negace, datový typ výsledku je `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="23554-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="23554-124">Pro bitovou negaci datový typ výsledku je stejný jako u `expression`.</span><span class="sxs-lookup"><span data-stu-id="23554-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="23554-125">Nicméně pokud je výraz `Decimal`, výsledkem je `Long`.</span><span class="sxs-lookup"><span data-stu-id="23554-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="23554-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="23554-126">Overloading</span></span>  
 <span data-ttu-id="23554-127">`Not` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="23554-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="23554-128">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="23554-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="23554-129">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="23554-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23554-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="23554-130">Example</span></span>  
 <span data-ttu-id="23554-131">V následujícím příkladu `Not` operátor logické negace na `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="23554-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="23554-132">Výsledkem je `Boolean` hodnotu, která představuje naopak hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="23554-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="23554-133">Předchozí příklad vytváří výsledky `False` a `True`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="23554-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23554-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="23554-134">Example</span></span>  
 <span data-ttu-id="23554-135">V následujícím příkladu `Not` operátor logické negace jednotlivých bitů číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="23554-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="23554-136">Bitového vzoru výsledek je nastavena pro stornování odpovídající bit v operandu modelu, včetně bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="23554-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="23554-137">V předchozím příkladu vytvoří výsledky – 11, –9 a –7, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="23554-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23554-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23554-138">See also</span></span>

- [<span data-ttu-id="23554-139">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23554-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="23554-140">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23554-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="23554-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="23554-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="23554-142">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23554-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
