---
title: Or – operátor (Visual Basic)
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
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955842"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="92738-102">Or – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92738-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="92738-103">Provede logickou disjunkci dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="92738-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92738-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92738-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="92738-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="92738-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="92738-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="92738-106">Required.</span></span> <span data-ttu-id="92738-107">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="92738-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="92738-108">Pro `Boolean` `Boolean` porovnání jecelkoválogickádisjunkcedvouhodnot.`result`</span><span class="sxs-lookup"><span data-stu-id="92738-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="92738-109">U bitových operací `result` je číselná hodnota, která představuje celkové disjunkci dvou číselných bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="92738-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="92738-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="92738-110">Required.</span></span> <span data-ttu-id="92738-111">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="92738-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="92738-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="92738-112">Required.</span></span> <span data-ttu-id="92738-113">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="92738-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92738-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92738-114">Remarks</span></span>  
 <span data-ttu-id="92738-115">Pro `Boolean` `expression1` `expression2` porovnání je if`False`a jenom v případě, že a vyhodnotí. `False` `result`</span><span class="sxs-lookup"><span data-stu-id="92738-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="92738-116">Následující tabulka ukazuje, jak `result` je určena.</span><span class="sxs-lookup"><span data-stu-id="92738-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="92738-117">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="92738-117">If `expression1` is</span></span>|<span data-ttu-id="92738-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="92738-118">And `expression2` is</span></span>|<span data-ttu-id="92738-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="92738-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="92738-120">`Boolean` V porovnání`Or` , operátor vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur.</span><span class="sxs-lookup"><span data-stu-id="92738-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="92738-121">[Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) provádí *krátkodobé okruhy*, což znamená, že `expression1` Pokud je `True`, pak `expression2` není vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="92738-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="92738-122">U bitových operací `Or` operátor provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` závislosti na následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="92738-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="92738-123">Pokud je bit `expression1` v</span><span class="sxs-lookup"><span data-stu-id="92738-123">If bit in `expression1` is</span></span>|<span data-ttu-id="92738-124">A bit v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="92738-124">And bit in `expression2` is</span></span>|<span data-ttu-id="92738-125">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="92738-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="92738-126">1</span><span class="sxs-lookup"><span data-stu-id="92738-126">1</span></span>|<span data-ttu-id="92738-127">1</span><span class="sxs-lookup"><span data-stu-id="92738-127">1</span></span>|<span data-ttu-id="92738-128">1</span><span class="sxs-lookup"><span data-stu-id="92738-128">1</span></span>|  
|<span data-ttu-id="92738-129">1</span><span class="sxs-lookup"><span data-stu-id="92738-129">1</span></span>|<span data-ttu-id="92738-130">0</span><span class="sxs-lookup"><span data-stu-id="92738-130">0</span></span>|<span data-ttu-id="92738-131">1</span><span class="sxs-lookup"><span data-stu-id="92738-131">1</span></span>|  
|<span data-ttu-id="92738-132">0</span><span class="sxs-lookup"><span data-stu-id="92738-132">0</span></span>|<span data-ttu-id="92738-133">1</span><span class="sxs-lookup"><span data-stu-id="92738-133">1</span></span>|<span data-ttu-id="92738-134">1</span><span class="sxs-lookup"><span data-stu-id="92738-134">1</span></span>|  
|<span data-ttu-id="92738-135">0</span><span class="sxs-lookup"><span data-stu-id="92738-135">0</span></span>|<span data-ttu-id="92738-136">0</span><span class="sxs-lookup"><span data-stu-id="92738-136">0</span></span>|<span data-ttu-id="92738-137">0</span><span class="sxs-lookup"><span data-stu-id="92738-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="92738-138">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.</span><span class="sxs-lookup"><span data-stu-id="92738-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="92738-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="92738-139">Data Types</span></span>  
 <span data-ttu-id="92738-140">Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic `Boolean` Převede výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.</span><span class="sxs-lookup"><span data-stu-id="92738-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="92738-141">Pro porovnání je `Boolean`datový typ výsledku. `Boolean`</span><span class="sxs-lookup"><span data-stu-id="92738-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="92738-142">Pro bitové porovnání je výsledný datový typ číselný typ vhodný pro datové typy `expression1` a. `expression2`</span><span class="sxs-lookup"><span data-stu-id="92738-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="92738-143">Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="92738-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="92738-144">Přetížení</span><span class="sxs-lookup"><span data-stu-id="92738-144">Overloading</span></span>  
 <span data-ttu-id="92738-145">Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `Or`</span><span class="sxs-lookup"><span data-stu-id="92738-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="92738-146">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="92738-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="92738-147">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="92738-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92738-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="92738-148">Example</span></span>  
 <span data-ttu-id="92738-149">Následující příklad používá `Or` operátor k provedení logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="92738-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="92738-150">Výsledkem je `Boolean` hodnota, která představuje, zda je `True`jeden z obou výrazů.</span><span class="sxs-lookup"><span data-stu-id="92738-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="92738-151">Předchozí příklad vytvoří výsledky `True`, `True`a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="92738-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92738-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="92738-152">Example</span></span>  
 <span data-ttu-id="92738-153">Následující příklad používá `Or` operátor k provedení celkového logického disjunkce na jednotlivých bitech dvou číselných výrazů.</span><span class="sxs-lookup"><span data-stu-id="92738-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="92738-154">Bit ve vzorci výsledků je nastaven, pokud je jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="92738-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="92738-155">Předchozí příklad vytvoří výsledky 10, 14 a 14 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="92738-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92738-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92738-156">See also</span></span>

- [<span data-ttu-id="92738-157">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92738-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="92738-158">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92738-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="92738-159">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="92738-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="92738-160">Operátor OrElse</span><span class="sxs-lookup"><span data-stu-id="92738-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="92738-161">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92738-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
