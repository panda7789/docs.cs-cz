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
ms.openlocfilehash: 999050314d674fa98833083d84796e471c22971d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406337"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="9024b-102">Xor – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9024b-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="9024b-103">Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="9024b-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9024b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9024b-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9024b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9024b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9024b-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9024b-106">Required.</span></span> <span data-ttu-id="9024b-107">Jakákoli `Boolean` nebo číselná proměnná.</span><span class="sxs-lookup"><span data-stu-id="9024b-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="9024b-108">Pro logické porovnání `result` je logické vyloučení (exkluzivní logická disjunkce) dvou `Boolean` hodnot.</span><span class="sxs-lookup"><span data-stu-id="9024b-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="9024b-109">U bitových operací `result` je číselná hodnota, která představuje bitové vyloučení (exkluzivní bitovou disjunkci) dvou číselných bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="9024b-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="9024b-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9024b-110">Required.</span></span> <span data-ttu-id="9024b-111">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="9024b-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9024b-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9024b-112">Required.</span></span> <span data-ttu-id="9024b-113">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="9024b-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9024b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9024b-114">Remarks</span></span>  
 <span data-ttu-id="9024b-115">Pro logické porovnání `result` je `True` if a pouze, pokud je přesně jeden z `expression1` a `expression2` vyhodnocen jako `True` .</span><span class="sxs-lookup"><span data-stu-id="9024b-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="9024b-116">To znamená, že pokud a `expression1` `expression2` vyhodnotí na opačné `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9024b-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="9024b-117">Následující tabulka ukazuje, jak `result` je určena.</span><span class="sxs-lookup"><span data-stu-id="9024b-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9024b-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="9024b-118">If `expression1` is</span></span>|<span data-ttu-id="9024b-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="9024b-119">And `expression2` is</span></span>|<span data-ttu-id="9024b-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="9024b-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="9024b-121">V porovnání s logickou hodnotou `Xor` operátor vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur.</span><span class="sxs-lookup"><span data-stu-id="9024b-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="9024b-122">Neexistují žádné krátkodobé protějšky k `Xor` , protože výsledek vždy závisí na obou operandech.</span><span class="sxs-lookup"><span data-stu-id="9024b-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="9024b-123">Pro logické operátory *krátkodobého okruhu* , viz [operátor AndAlso –](andalso-operator.md) a [operátor OrElse](orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9024b-123">For *short-circuiting* logical operators, see [AndAlso Operator](andalso-operator.md) and [OrElse Operator](orelse-operator.md).</span></span>  
  
 <span data-ttu-id="9024b-124">U bitových operací `Xor` operátor provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` závislosti na následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9024b-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="9024b-125">Pokud je bit v `expression1`</span><span class="sxs-lookup"><span data-stu-id="9024b-125">If bit in `expression1` is</span></span>|<span data-ttu-id="9024b-126">A bit v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="9024b-126">And bit in `expression2` is</span></span>|<span data-ttu-id="9024b-127">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="9024b-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="9024b-128">1</span><span class="sxs-lookup"><span data-stu-id="9024b-128">1</span></span>|<span data-ttu-id="9024b-129">1</span><span class="sxs-lookup"><span data-stu-id="9024b-129">1</span></span>|<span data-ttu-id="9024b-130">0</span><span class="sxs-lookup"><span data-stu-id="9024b-130">0</span></span>|  
|<span data-ttu-id="9024b-131">1</span><span class="sxs-lookup"><span data-stu-id="9024b-131">1</span></span>|<span data-ttu-id="9024b-132">0</span><span class="sxs-lookup"><span data-stu-id="9024b-132">0</span></span>|<span data-ttu-id="9024b-133">1</span><span class="sxs-lookup"><span data-stu-id="9024b-133">1</span></span>|  
|<span data-ttu-id="9024b-134">0</span><span class="sxs-lookup"><span data-stu-id="9024b-134">0</span></span>|<span data-ttu-id="9024b-135">1</span><span class="sxs-lookup"><span data-stu-id="9024b-135">1</span></span>|<span data-ttu-id="9024b-136">1</span><span class="sxs-lookup"><span data-stu-id="9024b-136">1</span></span>|  
|<span data-ttu-id="9024b-137">0</span><span class="sxs-lookup"><span data-stu-id="9024b-137">0</span></span>|<span data-ttu-id="9024b-138">0</span><span class="sxs-lookup"><span data-stu-id="9024b-138">0</span></span>|<span data-ttu-id="9024b-139">0</span><span class="sxs-lookup"><span data-stu-id="9024b-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9024b-140">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.</span><span class="sxs-lookup"><span data-stu-id="9024b-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="9024b-141">Například 5 `Xor` 3 je 6.</span><span class="sxs-lookup"><span data-stu-id="9024b-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="9024b-142">Chcete-li zjistit, proč je to tak, převeďte 5 a 3 na jejich binární reprezentace, 101 a 011.</span><span class="sxs-lookup"><span data-stu-id="9024b-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="9024b-143">Pak pomocí předchozí tabulky určete, že 101 XOR 011 je 110, což je binární reprezentace desítkového čísla 6.</span><span class="sxs-lookup"><span data-stu-id="9024b-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9024b-144">Typy dat</span><span class="sxs-lookup"><span data-stu-id="9024b-144">Data Types</span></span>  
 <span data-ttu-id="9024b-145">Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False` ) a provede bitovou operaci.</span><span class="sxs-lookup"><span data-stu-id="9024b-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="9024b-146">Pro `Boolean` porovnání je datový typ výsledku `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="9024b-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="9024b-147">Pro bitové porovnání je výsledný datový typ číselný typ vhodný pro datové typy `expression1` a `expression2` .</span><span class="sxs-lookup"><span data-stu-id="9024b-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9024b-148">Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="9024b-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9024b-149">Přetížení</span><span class="sxs-lookup"><span data-stu-id="9024b-149">Overloading</span></span>  
 <span data-ttu-id="9024b-150">`Xor`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9024b-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9024b-151">Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="9024b-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="9024b-152">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9024b-152">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9024b-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="9024b-153">Example</span></span>  
 <span data-ttu-id="9024b-154">Následující příklad používá `Xor` operátor k provedení logického vyloučení (exkluzivní logická disjunkce) na dvou výrazech.</span><span class="sxs-lookup"><span data-stu-id="9024b-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="9024b-155">Výsledkem je `Boolean` hodnota, která představuje, zda je přesně jeden z výrazů `True` .</span><span class="sxs-lookup"><span data-stu-id="9024b-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="9024b-156">Předchozí příklad vytvoří výsledky `False` , a v `True` `False` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9024b-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9024b-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="9024b-157">Example</span></span>  
 <span data-ttu-id="9024b-158">Následující příklad používá `Xor` operátor k provedení logického vyloučení (exkluzivní logická disjunkce) na jednotlivých bitech dvou číselných výrazů.</span><span class="sxs-lookup"><span data-stu-id="9024b-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="9024b-159">Bit ve vzorci výsledků je nastaven, pokud je přesně jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="9024b-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="9024b-160">Předchozí příklad vytvoří výsledky 2, 12 a 14 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9024b-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9024b-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="9024b-161">See also</span></span>

- [<span data-ttu-id="9024b-162">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9024b-162">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="9024b-163">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9024b-163">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="9024b-164">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="9024b-164">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="9024b-165">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9024b-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
