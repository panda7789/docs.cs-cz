---
title: And – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
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
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913160"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="a364a-102">And – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a364a-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="a364a-103">Provede logickou kombinaci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="a364a-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a364a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a364a-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a364a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a364a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a364a-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a364a-106">Required.</span></span> <span data-ttu-id="a364a-107">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="a364a-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="a364a-108">Pro logické porovnání `result` je logické spojení dvou `Boolean` hodnot.</span><span class="sxs-lookup"><span data-stu-id="a364a-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="a364a-109">U bitových operací `result` je číselná hodnota představující bitovou kombinaci dvou číselných bitových vzorů.</span><span class="sxs-lookup"><span data-stu-id="a364a-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a364a-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a364a-110">Required.</span></span> <span data-ttu-id="a364a-111">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="a364a-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a364a-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a364a-112">Required.</span></span> <span data-ttu-id="a364a-113">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="a364a-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a364a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a364a-114">Remarks</span></span>  
 <span data-ttu-id="a364a-115">Pro logické `result` porovnání je `expression2` `True` `expression1` `True` if a jenom v případě, že a vyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="a364a-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="a364a-116">Následující tabulka ukazuje, jak `result` je určena.</span><span class="sxs-lookup"><span data-stu-id="a364a-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a364a-117">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="a364a-117">If `expression1` is</span></span>|<span data-ttu-id="a364a-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="a364a-118">And `expression2` is</span></span>|<span data-ttu-id="a364a-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="a364a-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="a364a-120">V porovnání `And` s logickou hodnotou operátor vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur.</span><span class="sxs-lookup"><span data-stu-id="a364a-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a364a-121">[Operátor AndAlso –](../../../visual-basic/language-reference/operators/andalso-operator.md) provádí *krátkodobé okruhy*, což znamená, že `expression1` Pokud je `False`, pak `expression2` není vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="a364a-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="a364a-122">Při použití na číselné hodnoty `And` používá operátor bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastaví odpovídající bit v `result` závislosti na následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a364a-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a364a-123">Pokud je bit `expression1` v</span><span class="sxs-lookup"><span data-stu-id="a364a-123">If bit in `expression1` is</span></span>|<span data-ttu-id="a364a-124">A bit v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="a364a-124">And bit in `expression2` is</span></span>|<span data-ttu-id="a364a-125">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="a364a-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a364a-126">1</span><span class="sxs-lookup"><span data-stu-id="a364a-126">1</span></span>|<span data-ttu-id="a364a-127">1</span><span class="sxs-lookup"><span data-stu-id="a364a-127">1</span></span>|<span data-ttu-id="a364a-128">1</span><span class="sxs-lookup"><span data-stu-id="a364a-128">1</span></span>|  
|<span data-ttu-id="a364a-129">1</span><span class="sxs-lookup"><span data-stu-id="a364a-129">1</span></span>|<span data-ttu-id="a364a-130">0</span><span class="sxs-lookup"><span data-stu-id="a364a-130">0</span></span>|<span data-ttu-id="a364a-131">0</span><span class="sxs-lookup"><span data-stu-id="a364a-131">0</span></span>|  
|<span data-ttu-id="a364a-132">0</span><span class="sxs-lookup"><span data-stu-id="a364a-132">0</span></span>|<span data-ttu-id="a364a-133">1</span><span class="sxs-lookup"><span data-stu-id="a364a-133">1</span></span>|<span data-ttu-id="a364a-134">0</span><span class="sxs-lookup"><span data-stu-id="a364a-134">0</span></span>|  
|<span data-ttu-id="a364a-135">0</span><span class="sxs-lookup"><span data-stu-id="a364a-135">0</span></span>|<span data-ttu-id="a364a-136">0</span><span class="sxs-lookup"><span data-stu-id="a364a-136">0</span></span>|<span data-ttu-id="a364a-137">0</span><span class="sxs-lookup"><span data-stu-id="a364a-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a364a-138">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby se zajistily přesné výsledky.</span><span class="sxs-lookup"><span data-stu-id="a364a-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a364a-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a364a-139">Data Types</span></span>  
 <span data-ttu-id="a364a-140">Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic `Boolean` Převede výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.</span><span class="sxs-lookup"><span data-stu-id="a364a-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a364a-141">Pro logické porovnání je `Boolean`datový typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="a364a-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a364a-142">Pro bitové porovnání je výsledný datový typ číselný typ vhodný pro datové typy `expression1` a. `expression2`</span><span class="sxs-lookup"><span data-stu-id="a364a-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a364a-143">Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="a364a-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a364a-144">Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `And`</span><span class="sxs-lookup"><span data-stu-id="a364a-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a364a-145">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="a364a-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a364a-146">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a364a-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a364a-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="a364a-147">Example</span></span>  
 <span data-ttu-id="a364a-148">Následující příklad používá `And` operátor k provedení logického spojení se dvěma výrazy.</span><span class="sxs-lookup"><span data-stu-id="a364a-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="a364a-149">Výsledkem je `Boolean` hodnota, která představuje, zda jsou `True`oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="a364a-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="a364a-150">Předchozí příklad vytvoří výsledky `True` a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a364a-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a364a-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="a364a-151">Example</span></span>  
 <span data-ttu-id="a364a-152">Následující příklad používá `And` operátor k provedení logického spojení na jednotlivých bitech dvou číselných výrazů.</span><span class="sxs-lookup"><span data-stu-id="a364a-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a364a-153">Bit ve vzorci výsledků je nastaven, pokud jsou odpovídající bity v operandech nastaveny na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="a364a-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="a364a-154">Předchozí příklad vytvoří výsledky 8, 2 a 0 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a364a-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a364a-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a364a-155">See also</span></span>

- [<span data-ttu-id="a364a-156">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a364a-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="a364a-157">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a364a-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a364a-158">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="a364a-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a364a-159">Operátor AndAlso</span><span class="sxs-lookup"><span data-stu-id="a364a-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="a364a-160">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a364a-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
