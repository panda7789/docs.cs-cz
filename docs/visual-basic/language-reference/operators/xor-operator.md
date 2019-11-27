---
title: Xor – operátor
ms.date: 07/20/2015
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
ms.openlocfilehash: c5c7ec87bc173f724f8c670395bc3b0458444df6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335402"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="0290e-102">Xor – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0290e-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="0290e-103">Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="0290e-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0290e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0290e-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0290e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0290e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0290e-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0290e-106">Required.</span></span> <span data-ttu-id="0290e-107">Jakákoli `Boolean` nebo číselná proměnná.</span><span class="sxs-lookup"><span data-stu-id="0290e-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="0290e-108">Pro logické porovnání je `result` logické vyloučení (exkluzivní logická disjunkce) dvou hodnot `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="0290e-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="0290e-109">U bitových operací je `result` číselná hodnota, která představuje bitové vyloučení (exkluzivní bitovou disjunkci) dvou číselných bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="0290e-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="0290e-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0290e-110">Required.</span></span> <span data-ttu-id="0290e-111">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="0290e-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0290e-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0290e-112">Required.</span></span> <span data-ttu-id="0290e-113">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="0290e-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0290e-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0290e-114">Remarks</span></span>  
 <span data-ttu-id="0290e-115">Pro účely logického porovnání je `result` `True`, pokud je přesně jedna z `expression1` a `expression2` vyhodnocena jako `True`.</span><span class="sxs-lookup"><span data-stu-id="0290e-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="0290e-116">To znamená, že pokud a pouze pokud `expression1` a `expression2` vyhodnoceny na opak `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0290e-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="0290e-117">Následující tabulka ukazuje, jak je určena `result`.</span><span class="sxs-lookup"><span data-stu-id="0290e-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0290e-118">Pokud je `expression1`</span><span class="sxs-lookup"><span data-stu-id="0290e-118">If `expression1` is</span></span>|<span data-ttu-id="0290e-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="0290e-119">And `expression2` is</span></span>|<span data-ttu-id="0290e-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="0290e-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="0290e-121">V porovnání s logickou hodnotou operátor `Xor` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur.</span><span class="sxs-lookup"><span data-stu-id="0290e-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="0290e-122">Neexistují žádné krátkodobé protějšky, které by bylo možné `Xor`, protože výsledek vždy závisí na obou operandech.</span><span class="sxs-lookup"><span data-stu-id="0290e-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="0290e-123">Pro logické operátory *krátkodobého okruhu* , viz [operátor AndAlso –](../../../visual-basic/language-reference/operators/andalso-operator.md) a [operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0290e-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="0290e-124">U bitových operací operátor `Xor` provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="0290e-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="0290e-125">Pokud je bit v `expression1`</span><span class="sxs-lookup"><span data-stu-id="0290e-125">If bit in `expression1` is</span></span>|<span data-ttu-id="0290e-126">A bit ve `expression2` je</span><span class="sxs-lookup"><span data-stu-id="0290e-126">And bit in `expression2` is</span></span>|<span data-ttu-id="0290e-127">Bit ve `result` je</span><span class="sxs-lookup"><span data-stu-id="0290e-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="0290e-128">1</span><span class="sxs-lookup"><span data-stu-id="0290e-128">1</span></span>|<span data-ttu-id="0290e-129">1</span><span class="sxs-lookup"><span data-stu-id="0290e-129">1</span></span>|<span data-ttu-id="0290e-130">0</span><span class="sxs-lookup"><span data-stu-id="0290e-130">0</span></span>|  
|<span data-ttu-id="0290e-131">1</span><span class="sxs-lookup"><span data-stu-id="0290e-131">1</span></span>|<span data-ttu-id="0290e-132">0</span><span class="sxs-lookup"><span data-stu-id="0290e-132">0</span></span>|<span data-ttu-id="0290e-133">1</span><span class="sxs-lookup"><span data-stu-id="0290e-133">1</span></span>|  
|<span data-ttu-id="0290e-134">0</span><span class="sxs-lookup"><span data-stu-id="0290e-134">0</span></span>|<span data-ttu-id="0290e-135">1</span><span class="sxs-lookup"><span data-stu-id="0290e-135">1</span></span>|<span data-ttu-id="0290e-136">1</span><span class="sxs-lookup"><span data-stu-id="0290e-136">1</span></span>|  
|<span data-ttu-id="0290e-137">0</span><span class="sxs-lookup"><span data-stu-id="0290e-137">0</span></span>|<span data-ttu-id="0290e-138">0</span><span class="sxs-lookup"><span data-stu-id="0290e-138">0</span></span>|<span data-ttu-id="0290e-139">0</span><span class="sxs-lookup"><span data-stu-id="0290e-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0290e-140">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.</span><span class="sxs-lookup"><span data-stu-id="0290e-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="0290e-141">Například 5 `Xor` 3 je 6.</span><span class="sxs-lookup"><span data-stu-id="0290e-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="0290e-142">Chcete-li zjistit, proč je to tak, převeďte 5 a 3 na jejich binární reprezentace, 101 a 011.</span><span class="sxs-lookup"><span data-stu-id="0290e-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="0290e-143">Pak pomocí předchozí tabulky určete, že 101 XOR 011 je 110, což je binární reprezentace desítkového čísla 6.</span><span class="sxs-lookup"><span data-stu-id="0290e-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="0290e-144">Datové typy</span><span class="sxs-lookup"><span data-stu-id="0290e-144">Data Types</span></span>  
 <span data-ttu-id="0290e-145">Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.</span><span class="sxs-lookup"><span data-stu-id="0290e-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="0290e-146">Pro porovnání `Boolean` je datový typ výsledku `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="0290e-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="0290e-147">Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="0290e-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="0290e-148">Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="0290e-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0290e-149">Přetížení</span><span class="sxs-lookup"><span data-stu-id="0290e-149">Overloading</span></span>  
 <span data-ttu-id="0290e-150">Operátor `Xor` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0290e-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0290e-151">Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="0290e-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="0290e-152">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0290e-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0290e-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="0290e-153">Example</span></span>  
 <span data-ttu-id="0290e-154">Následující příklad používá operátor `Xor` k provedení logického vyloučení (exkluzivní logická disjunkce) na dvou výrazech.</span><span class="sxs-lookup"><span data-stu-id="0290e-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="0290e-155">Výsledkem je `Boolean` hodnota, která představuje, zda je právě jeden z výrazů `True`.</span><span class="sxs-lookup"><span data-stu-id="0290e-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="0290e-156">Předchozí příklad vytvoří výsledky `False`, `True`a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0290e-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0290e-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="0290e-157">Example</span></span>  
 <span data-ttu-id="0290e-158">Následující příklad používá operátor `Xor` k provedení logického vyloučení (exkluzivní logická disjunkce) na jednotlivých bitech dvou číselných výrazů.</span><span class="sxs-lookup"><span data-stu-id="0290e-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="0290e-159">Bit ve vzorci výsledků je nastaven, pokud je přesně jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="0290e-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="0290e-160">Předchozí příklad vytvoří výsledky 2, 12 a 14 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0290e-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0290e-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0290e-161">See also</span></span>

- [<span data-ttu-id="0290e-162">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0290e-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="0290e-163">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0290e-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0290e-164">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0290e-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0290e-165">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0290e-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
