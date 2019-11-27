---
title: Or – operátor
ms.date: 07/20/2015
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
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348254"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="efdae-102">Or – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efdae-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="efdae-103">Provede logickou disjunkci dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="efdae-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efdae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efdae-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="efdae-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="efdae-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="efdae-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="efdae-106">Required.</span></span> <span data-ttu-id="efdae-107">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="efdae-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="efdae-108">Pro účely porovnání `Boolean` `result` je logickým disjunkci dvou `Boolean` hodnot.</span><span class="sxs-lookup"><span data-stu-id="efdae-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="efdae-109">V případě bitových operací je `result` číselná hodnota představující celkovou bitovou disjunkci dvou číselných bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="efdae-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="efdae-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="efdae-110">Required.</span></span> <span data-ttu-id="efdae-111">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="efdae-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="efdae-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="efdae-112">Required.</span></span> <span data-ttu-id="efdae-113">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="efdae-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efdae-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efdae-114">Remarks</span></span>  
 <span data-ttu-id="efdae-115">Pro porovnání `Boolean` `result` je `False` pouze v případě, že `expression1` a `expression2` vyhodnocena jako `False`.</span><span class="sxs-lookup"><span data-stu-id="efdae-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="efdae-116">Následující tabulka ukazuje, jak je určena `result`.</span><span class="sxs-lookup"><span data-stu-id="efdae-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="efdae-117">Pokud je `expression1`</span><span class="sxs-lookup"><span data-stu-id="efdae-117">If `expression1` is</span></span>|<span data-ttu-id="efdae-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="efdae-118">And `expression2` is</span></span>|<span data-ttu-id="efdae-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="efdae-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="efdae-120">V porovnání `Boolean` operátor `Or` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur.</span><span class="sxs-lookup"><span data-stu-id="efdae-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="efdae-121">[Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud je `expression1` `True`, `expression2` není vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="efdae-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="efdae-122">U bitových operací operátor `Or` provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="efdae-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="efdae-123">Pokud je bit v `expression1`</span><span class="sxs-lookup"><span data-stu-id="efdae-123">If bit in `expression1` is</span></span>|<span data-ttu-id="efdae-124">A bit ve `expression2` je</span><span class="sxs-lookup"><span data-stu-id="efdae-124">And bit in `expression2` is</span></span>|<span data-ttu-id="efdae-125">Bit ve `result` je</span><span class="sxs-lookup"><span data-stu-id="efdae-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="efdae-126">1</span><span class="sxs-lookup"><span data-stu-id="efdae-126">1</span></span>|<span data-ttu-id="efdae-127">1</span><span class="sxs-lookup"><span data-stu-id="efdae-127">1</span></span>|<span data-ttu-id="efdae-128">1</span><span class="sxs-lookup"><span data-stu-id="efdae-128">1</span></span>|  
|<span data-ttu-id="efdae-129">1</span><span class="sxs-lookup"><span data-stu-id="efdae-129">1</span></span>|<span data-ttu-id="efdae-130">0</span><span class="sxs-lookup"><span data-stu-id="efdae-130">0</span></span>|<span data-ttu-id="efdae-131">1</span><span class="sxs-lookup"><span data-stu-id="efdae-131">1</span></span>|  
|<span data-ttu-id="efdae-132">0</span><span class="sxs-lookup"><span data-stu-id="efdae-132">0</span></span>|<span data-ttu-id="efdae-133">1</span><span class="sxs-lookup"><span data-stu-id="efdae-133">1</span></span>|<span data-ttu-id="efdae-134">1</span><span class="sxs-lookup"><span data-stu-id="efdae-134">1</span></span>|  
|<span data-ttu-id="efdae-135">0</span><span class="sxs-lookup"><span data-stu-id="efdae-135">0</span></span>|<span data-ttu-id="efdae-136">0</span><span class="sxs-lookup"><span data-stu-id="efdae-136">0</span></span>|<span data-ttu-id="efdae-137">0</span><span class="sxs-lookup"><span data-stu-id="efdae-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="efdae-138">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.</span><span class="sxs-lookup"><span data-stu-id="efdae-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="efdae-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="efdae-139">Data Types</span></span>  
 <span data-ttu-id="efdae-140">Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.</span><span class="sxs-lookup"><span data-stu-id="efdae-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="efdae-141">Pro porovnání `Boolean` je datový typ výsledku `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="efdae-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="efdae-142">Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="efdae-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="efdae-143">Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="efdae-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="efdae-144">Přetížení</span><span class="sxs-lookup"><span data-stu-id="efdae-144">Overloading</span></span>  
 <span data-ttu-id="efdae-145">Operátor `Or` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="efdae-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="efdae-146">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="efdae-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="efdae-147">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="efdae-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="efdae-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="efdae-148">Example</span></span>  
 <span data-ttu-id="efdae-149">Následující příklad používá operátor `Or` k provedení celkové logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="efdae-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="efdae-150">Výsledkem je `Boolean` hodnota, která představuje, zda je jeden z obou výrazů `True`.</span><span class="sxs-lookup"><span data-stu-id="efdae-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="efdae-151">Předchozí příklad vytvoří výsledky `True`, `True`a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="efdae-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efdae-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="efdae-152">Example</span></span>  
 <span data-ttu-id="efdae-153">Následující příklad používá operátor `Or` k provedení celkového logického disjunkce na jednotlivých bitech dvou číselných výrazů.</span><span class="sxs-lookup"><span data-stu-id="efdae-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="efdae-154">Bit ve vzorci výsledků je nastaven, pokud je jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="efdae-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="efdae-155">Předchozí příklad vytvoří výsledky 10, 14 a 14 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="efdae-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efdae-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efdae-156">See also</span></span>

- [<span data-ttu-id="efdae-157">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efdae-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="efdae-158">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efdae-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="efdae-159">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="efdae-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="efdae-160">Operátor OrElse</span><span class="sxs-lookup"><span data-stu-id="efdae-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="efdae-161">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efdae-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
