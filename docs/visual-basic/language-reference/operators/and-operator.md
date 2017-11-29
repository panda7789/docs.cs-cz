---
title: "And – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="d1916-102">And – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1916-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="d1916-103">Provede logickou konjunkci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="d1916-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1916-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1916-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="d1916-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d1916-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d1916-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d1916-106">Required.</span></span> <span data-ttu-id="d1916-107">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="d1916-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="d1916-108">Pro logickou porovnání `result` je logickou konjunkci dvou `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1916-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="d1916-109">Pro bitové operace `result` je číselná hodnota představující bitové spojení dvou bit číselná vzory.</span><span class="sxs-lookup"><span data-stu-id="d1916-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="d1916-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d1916-110">Required.</span></span> <span data-ttu-id="d1916-111">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="d1916-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="d1916-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d1916-112">Required.</span></span> <span data-ttu-id="d1916-113">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="d1916-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1916-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1916-114">Remarks</span></span>  
 <span data-ttu-id="d1916-115">Pro logickou porovnání `result` je `True` případě a pouze v případě obou `expression1` a `expression2` vyhodnocení `True`.</span><span class="sxs-lookup"><span data-stu-id="d1916-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="d1916-116">Následující tabulka popisuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="d1916-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="d1916-117">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="d1916-117">If `expression1` is</span></span>|<span data-ttu-id="d1916-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="d1916-118">And `expression2` is</span></span>|<span data-ttu-id="d1916-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="d1916-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="d1916-120">Logická hodnota porovnání `And` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury.</span><span class="sxs-lookup"><span data-stu-id="d1916-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="d1916-121">[AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) provede *krátká smyčka*, což znamená, že pokud `expression1` je `False`, pak `expression2` , nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="d1916-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="d1916-122">Při použití číselné hodnoty, `And` operátor provádí bitové porovnání stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající chvíli v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="d1916-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="d1916-123">Pokud bit v `expression1` je</span><span class="sxs-lookup"><span data-stu-id="d1916-123">If bit in `expression1` is</span></span>|<span data-ttu-id="d1916-124">A chvíli v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="d1916-124">And bit in `expression2` is</span></span>|<span data-ttu-id="d1916-125">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="d1916-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="d1916-126">1</span><span class="sxs-lookup"><span data-stu-id="d1916-126">1</span></span>|<span data-ttu-id="d1916-127">1</span><span class="sxs-lookup"><span data-stu-id="d1916-127">1</span></span>|<span data-ttu-id="d1916-128">1</span><span class="sxs-lookup"><span data-stu-id="d1916-128">1</span></span>|  
|<span data-ttu-id="d1916-129">1</span><span class="sxs-lookup"><span data-stu-id="d1916-129">1</span></span>|<span data-ttu-id="d1916-130">0</span><span class="sxs-lookup"><span data-stu-id="d1916-130">0</span></span>|<span data-ttu-id="d1916-131">0</span><span class="sxs-lookup"><span data-stu-id="d1916-131">0</span></span>|  
|<span data-ttu-id="d1916-132">0</span><span class="sxs-lookup"><span data-stu-id="d1916-132">0</span></span>|<span data-ttu-id="d1916-133">1</span><span class="sxs-lookup"><span data-stu-id="d1916-133">1</span></span>|<span data-ttu-id="d1916-134">0</span><span class="sxs-lookup"><span data-stu-id="d1916-134">0</span></span>|  
|<span data-ttu-id="d1916-135">0</span><span class="sxs-lookup"><span data-stu-id="d1916-135">0</span></span>|<span data-ttu-id="d1916-136">0</span><span class="sxs-lookup"><span data-stu-id="d1916-136">0</span></span>|<span data-ttu-id="d1916-137">0</span><span class="sxs-lookup"><span data-stu-id="d1916-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d1916-138">Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách zajistit přesné výsledky.</span><span class="sxs-lookup"><span data-stu-id="d1916-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="d1916-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="d1916-139">Data Types</span></span>  
 <span data-ttu-id="d1916-140">Pokud operandy skládá z jedné `Boolean` výraz a jeden číselného výrazu jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (-1 pro `True` a 0 pro `False`) a provede se bitová operace.</span><span class="sxs-lookup"><span data-stu-id="d1916-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="d1916-141">Logická hodnota porovnání, datový typ výsledku je `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d1916-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="d1916-142">Bitové porovnání, výsledek datový typ je vhodný pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="d1916-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="d1916-143">Podívejte se na tabulku "Relační bitový porovnání a" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="d1916-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1916-144">`And` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="d1916-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d1916-145">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="d1916-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d1916-146">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d1916-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1916-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1916-147">Example</span></span>  
 <span data-ttu-id="d1916-148">Následující příklad používá `And` operátor provést logickou konjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="d1916-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="d1916-149">Výsledkem je, `Boolean` hodnotu, která udává, zda jsou obě výrazy `True`.</span><span class="sxs-lookup"><span data-stu-id="d1916-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="d1916-150">V předchozím příkladu vytvoří výsledky `True` a `False`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d1916-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1916-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1916-151">Example</span></span>  
 <span data-ttu-id="d1916-152">Následující příklad používá `And` operátor k provedení logické spojení na jednotlivé bity dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="d1916-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="d1916-153">Pokud odpovídající bity v operandy jsou obě nastavena na hodnotu 1, je nastaven bit ve vzoru výsledek.</span><span class="sxs-lookup"><span data-stu-id="d1916-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="d1916-154">V předchozím příkladu poskytuje výsledky 8, 2 a 0, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d1916-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1916-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1916-155">See Also</span></span>  
 [<span data-ttu-id="d1916-156">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1916-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="d1916-157">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1916-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d1916-158">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="d1916-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d1916-159">AndAlso – operátor</span><span class="sxs-lookup"><span data-stu-id="d1916-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="d1916-160">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1916-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
