---
title: Or – operátor (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c9429eb2bdeb86bfa73786433231fdc22a230d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="a14d6-102">Or – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a14d6-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="a14d6-103">Provede logické disjunkce dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="a14d6-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a14d6-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a14d6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a14d6-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a14d6-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a14d6-106">Required.</span></span> <span data-ttu-id="a14d6-107">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a14d6-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="a14d6-108">Pro `Boolean` porovnání, `result` je včetně logické disjunkce dvou `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a14d6-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="a14d6-109">Pro bitové operace `result` je číselná hodnota představující včetně bitovou disjunkci dvou bit číselná vzory.</span><span class="sxs-lookup"><span data-stu-id="a14d6-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a14d6-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a14d6-110">Required.</span></span> <span data-ttu-id="a14d6-111">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a14d6-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a14d6-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a14d6-112">Required.</span></span> <span data-ttu-id="a14d6-113">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a14d6-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a14d6-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a14d6-114">Remarks</span></span>  
 <span data-ttu-id="a14d6-115">Pro `Boolean` porovnání, `result` je `False` případě a pouze v případě obou `expression1` a `expression2` vyhodnocení `False`.</span><span class="sxs-lookup"><span data-stu-id="a14d6-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="a14d6-116">Následující tabulka popisuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="a14d6-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a14d6-117">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="a14d6-117">If `expression1` is</span></span>|<span data-ttu-id="a14d6-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="a14d6-118">And `expression2` is</span></span>|<span data-ttu-id="a14d6-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="a14d6-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="a14d6-120">V `Boolean` porovnání, `Or` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury.</span><span class="sxs-lookup"><span data-stu-id="a14d6-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a14d6-121">[Orelse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md) provede *krátká smyčka*, což znamená, že pokud `expression1` je `True`, pak `expression2` , nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="a14d6-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="a14d6-122">Pro bitové operace `Or` operátor provádí bitové porovnání stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající chvíli v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="a14d6-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a14d6-123">Pokud bit v `expression1` je</span><span class="sxs-lookup"><span data-stu-id="a14d6-123">If bit in `expression1` is</span></span>|<span data-ttu-id="a14d6-124">A chvíli v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="a14d6-124">And bit in `expression2` is</span></span>|<span data-ttu-id="a14d6-125">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="a14d6-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a14d6-126">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-126">1</span></span>|<span data-ttu-id="a14d6-127">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-127">1</span></span>|<span data-ttu-id="a14d6-128">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-128">1</span></span>|  
|<span data-ttu-id="a14d6-129">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-129">1</span></span>|<span data-ttu-id="a14d6-130">0</span><span class="sxs-lookup"><span data-stu-id="a14d6-130">0</span></span>|<span data-ttu-id="a14d6-131">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-131">1</span></span>|  
|<span data-ttu-id="a14d6-132">0</span><span class="sxs-lookup"><span data-stu-id="a14d6-132">0</span></span>|<span data-ttu-id="a14d6-133">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-133">1</span></span>|<span data-ttu-id="a14d6-134">1</span><span class="sxs-lookup"><span data-stu-id="a14d6-134">1</span></span>|  
|<span data-ttu-id="a14d6-135">0</span><span class="sxs-lookup"><span data-stu-id="a14d6-135">0</span></span>|<span data-ttu-id="a14d6-136">0</span><span class="sxs-lookup"><span data-stu-id="a14d6-136">0</span></span>|<span data-ttu-id="a14d6-137">0</span><span class="sxs-lookup"><span data-stu-id="a14d6-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a14d6-138">Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách a zajišťují přesné provádění.</span><span class="sxs-lookup"><span data-stu-id="a14d6-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a14d6-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a14d6-139">Data Types</span></span>  
 <span data-ttu-id="a14d6-140">Pokud operandy skládá z jedné `Boolean` výraz a jeden číselného výrazu jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (-1 pro `True` a 0 pro `False`) a provede se bitová operace.</span><span class="sxs-lookup"><span data-stu-id="a14d6-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a14d6-141">Pro `Boolean` je datový typ výsledku porovnání, `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a14d6-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a14d6-142">Bitové porovnání, výsledek datový typ je vhodný pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="a14d6-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a14d6-143">Podívejte se na tabulku "Relační bitový porovnání a" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="a14d6-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a14d6-144">Přetížení</span><span class="sxs-lookup"><span data-stu-id="a14d6-144">Overloading</span></span>  
 <span data-ttu-id="a14d6-145">`Or` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="a14d6-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a14d6-146">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="a14d6-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a14d6-147">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a14d6-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a14d6-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="a14d6-148">Example</span></span>  
 <span data-ttu-id="a14d6-149">Následující příklad používá `Or` operátor provést včetně logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="a14d6-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="a14d6-150">Výsledkem je, `Boolean` hodnotu, která představuje zda je jedna ze dvou výrazů `True`.</span><span class="sxs-lookup"><span data-stu-id="a14d6-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 <span data-ttu-id="a14d6-151">V předchozím příkladu vytvoří výsledky `True`, `True`, a `False`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a14d6-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a14d6-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="a14d6-152">Example</span></span>  
 <span data-ttu-id="a14d6-153">Následující příklad používá `Or` operátor provést včetně logické disjunkce na jednotlivé bity dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="a14d6-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a14d6-154">Pokud je buď odpovídající bity operandy nastavená na hodnotu 1, je nastaven bit ve vzoru výsledek.</span><span class="sxs-lookup"><span data-stu-id="a14d6-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 <span data-ttu-id="a14d6-155">V předchozím příkladu vytvoří výsledky 10, 14 a 14, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a14d6-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14d6-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="a14d6-156">See Also</span></span>  
 [<span data-ttu-id="a14d6-157">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a14d6-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="a14d6-158">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a14d6-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="a14d6-159">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="a14d6-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="a14d6-160">Orelse – operátor</span><span class="sxs-lookup"><span data-stu-id="a14d6-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [<span data-ttu-id="a14d6-161">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a14d6-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
