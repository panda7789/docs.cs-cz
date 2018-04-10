---
title: Xor – operátor (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="668e8-102">Xor – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="668e8-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="668e8-103">Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="668e8-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="668e8-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="668e8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="668e8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="668e8-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="668e8-106">Required.</span></span> <span data-ttu-id="668e8-107">Všechny `Boolean` nebo číselné proměnné.</span><span class="sxs-lookup"><span data-stu-id="668e8-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="668e8-108">Pro logickou porovnání `result` je logická exkluze (exkluzivní disjunkce logické) ze dvou `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="668e8-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="668e8-109">Pro bitové operace `result` je číselná hodnota, která představuje bitové vyloučení dvou bit číselná vzory (výhradní bitovou disjunkci).</span><span class="sxs-lookup"><span data-stu-id="668e8-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="668e8-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="668e8-110">Required.</span></span> <span data-ttu-id="668e8-111">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="668e8-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="668e8-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="668e8-112">Required.</span></span> <span data-ttu-id="668e8-113">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="668e8-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="668e8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="668e8-114">Remarks</span></span>  
 <span data-ttu-id="668e8-115">Pro logickou porovnání `result` je `True` jenom v případě právě jeden z `expression1` a `expression2` vyhodnocuje `True`.</span><span class="sxs-lookup"><span data-stu-id="668e8-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="668e8-116">To znamená jenom v případě `expression1` a `expression2` vyhodnocení na opačné `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="668e8-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="668e8-117">Následující tabulka popisuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="668e8-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="668e8-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="668e8-118">If `expression1` is</span></span>|<span data-ttu-id="668e8-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="668e8-119">And `expression2` is</span></span>|<span data-ttu-id="668e8-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="668e8-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="668e8-121">Logická hodnota porovnání `Xor` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury.</span><span class="sxs-lookup"><span data-stu-id="668e8-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="668e8-122">Neexistuje žádné short-circuiting protějškem `Xor`, protože výsledek je vždy závisí na oba operandy.</span><span class="sxs-lookup"><span data-stu-id="668e8-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="668e8-123">Pro *krátká smyčka* najdete v části logické operátory [AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) a [orelse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="668e8-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="668e8-124">Pro bitové operace `Xor` operátor provádí bitové porovnání stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající chvíli v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="668e8-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="668e8-125">Pokud bit v `expression1` je</span><span class="sxs-lookup"><span data-stu-id="668e8-125">If bit in `expression1` is</span></span>|<span data-ttu-id="668e8-126">A chvíli v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="668e8-126">And bit in `expression2` is</span></span>|<span data-ttu-id="668e8-127">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="668e8-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="668e8-128">1</span><span class="sxs-lookup"><span data-stu-id="668e8-128">1</span></span>|<span data-ttu-id="668e8-129">1</span><span class="sxs-lookup"><span data-stu-id="668e8-129">1</span></span>|<span data-ttu-id="668e8-130">0</span><span class="sxs-lookup"><span data-stu-id="668e8-130">0</span></span>|  
|<span data-ttu-id="668e8-131">1</span><span class="sxs-lookup"><span data-stu-id="668e8-131">1</span></span>|<span data-ttu-id="668e8-132">0</span><span class="sxs-lookup"><span data-stu-id="668e8-132">0</span></span>|<span data-ttu-id="668e8-133">1</span><span class="sxs-lookup"><span data-stu-id="668e8-133">1</span></span>|  
|<span data-ttu-id="668e8-134">0</span><span class="sxs-lookup"><span data-stu-id="668e8-134">0</span></span>|<span data-ttu-id="668e8-135">1</span><span class="sxs-lookup"><span data-stu-id="668e8-135">1</span></span>|<span data-ttu-id="668e8-136">1</span><span class="sxs-lookup"><span data-stu-id="668e8-136">1</span></span>|  
|<span data-ttu-id="668e8-137">0</span><span class="sxs-lookup"><span data-stu-id="668e8-137">0</span></span>|<span data-ttu-id="668e8-138">0</span><span class="sxs-lookup"><span data-stu-id="668e8-138">0</span></span>|<span data-ttu-id="668e8-139">0</span><span class="sxs-lookup"><span data-stu-id="668e8-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="668e8-140">Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách a zajišťují přesné provádění.</span><span class="sxs-lookup"><span data-stu-id="668e8-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="668e8-141">Například 5 `Xor` 3 je 6.</span><span class="sxs-lookup"><span data-stu-id="668e8-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="668e8-142">Zjistěte, proč to tedy převést na binární reprezentace 101 a 011 5 a 3.</span><span class="sxs-lookup"><span data-stu-id="668e8-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="668e8-143">V předchozí tabulce pak použije k určení, že 101 Xor 011 je 110, což je binární reprezentace desetinné číslo 6.</span><span class="sxs-lookup"><span data-stu-id="668e8-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="668e8-144">Datové typy</span><span class="sxs-lookup"><span data-stu-id="668e8-144">Data Types</span></span>  
 <span data-ttu-id="668e8-145">Pokud operandy skládá z jedné `Boolean` výraz a jeden číselného výrazu jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (-1 pro `True` a 0 pro `False`) a provede se bitová operace.</span><span class="sxs-lookup"><span data-stu-id="668e8-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="668e8-146">Pro `Boolean` je datový typ výsledku porovnání, `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="668e8-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="668e8-147">Bitové porovnání, výsledek datový typ je vhodný pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="668e8-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="668e8-148">Podívejte se na tabulku "Relační bitový porovnání a" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="668e8-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="668e8-149">Přetížení</span><span class="sxs-lookup"><span data-stu-id="668e8-149">Overloading</span></span>  
 <span data-ttu-id="668e8-150">`Xor` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="668e8-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="668e8-151">Pokud váš kód používá tento operátor. v takových třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="668e8-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="668e8-152">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="668e8-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="668e8-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="668e8-153">Example</span></span>  
 <span data-ttu-id="668e8-154">Následující příklad používá `Xor` operátor provést (exkluzivní disjunkce logické) logické vyloučení dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="668e8-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="668e8-155">Výsledkem je, `Boolean` hodnotu, která udává, zda přesně jeden z výrazů je `True`.</span><span class="sxs-lookup"><span data-stu-id="668e8-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 <span data-ttu-id="668e8-156">Předchozí příklad vytvoří výsledky `False`, `True`, a `False`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="668e8-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="668e8-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="668e8-157">Example</span></span>  
 <span data-ttu-id="668e8-158">Následující příklad používá `Xor` operátor k provedení logické vyloučení (exkluzivní disjunkce logické) na jednotlivé bity dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="668e8-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="668e8-159">Je-li přesně odpovídající bity operandy nastavena na hodnotu 1, je nastaven bit ve vzoru výsledek.</span><span class="sxs-lookup"><span data-stu-id="668e8-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 <span data-ttu-id="668e8-160">Předchozí příklad vytvoří výsledky 2, 12 a 14, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="668e8-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668e8-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="668e8-161">See Also</span></span>  
 [<span data-ttu-id="668e8-162">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="668e8-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="668e8-163">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="668e8-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="668e8-164">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="668e8-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="668e8-165">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="668e8-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
