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
ms.openlocfilehash: 7e25f25677fa684427bdaf00cea73916ffbad655
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608356"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="1facc-102">And – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1facc-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="1facc-103">Provede logickou konjunkci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="1facc-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1facc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1facc-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1facc-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1facc-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1facc-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1facc-106">Required.</span></span> <span data-ttu-id="1facc-107">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="1facc-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="1facc-108">Logická porovnání `result` je logickou konjunkci dvou `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1facc-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="1facc-109">Pro bitové operace `result` číselná hodnota představující bitové spojení dvou číselných bitové vzory.</span><span class="sxs-lookup"><span data-stu-id="1facc-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="1facc-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1facc-110">Required.</span></span> <span data-ttu-id="1facc-111">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="1facc-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1facc-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1facc-112">Required.</span></span> <span data-ttu-id="1facc-113">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="1facc-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1facc-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1facc-114">Remarks</span></span>  
 <span data-ttu-id="1facc-115">Logická porovnání `result` je `True` Pokud a pouze pokud oba `expression1` a `expression2` vyhodnotit `True`.</span><span class="sxs-lookup"><span data-stu-id="1facc-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="1facc-116">Následující tabulka ukazuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="1facc-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="1facc-117">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="1facc-117">If `expression1` is</span></span>|<span data-ttu-id="1facc-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="1facc-118">And `expression2` is</span></span>|<span data-ttu-id="1facc-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="1facc-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="1facc-120">Logická porovnání `And` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury.</span><span class="sxs-lookup"><span data-stu-id="1facc-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="1facc-121">[AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) provádí *zkrácenou*, což znamená, že pokud `expression1` je `False`, pak `expression2` , nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="1facc-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="1facc-122">Při použití u číselných hodnot `And` operátor provádí porovnání bitového stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající bit v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="1facc-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="1facc-123">Pokud bit v `expression1` je</span><span class="sxs-lookup"><span data-stu-id="1facc-123">If bit in `expression1` is</span></span>|<span data-ttu-id="1facc-124">A bitu v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="1facc-124">And bit in `expression2` is</span></span>|<span data-ttu-id="1facc-125">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="1facc-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="1facc-126">1</span><span class="sxs-lookup"><span data-stu-id="1facc-126">1</span></span>|<span data-ttu-id="1facc-127">1</span><span class="sxs-lookup"><span data-stu-id="1facc-127">1</span></span>|<span data-ttu-id="1facc-128">1</span><span class="sxs-lookup"><span data-stu-id="1facc-128">1</span></span>|  
|<span data-ttu-id="1facc-129">1</span><span class="sxs-lookup"><span data-stu-id="1facc-129">1</span></span>|<span data-ttu-id="1facc-130">0</span><span class="sxs-lookup"><span data-stu-id="1facc-130">0</span></span>|<span data-ttu-id="1facc-131">0</span><span class="sxs-lookup"><span data-stu-id="1facc-131">0</span></span>|  
|<span data-ttu-id="1facc-132">0</span><span class="sxs-lookup"><span data-stu-id="1facc-132">0</span></span>|<span data-ttu-id="1facc-133">1</span><span class="sxs-lookup"><span data-stu-id="1facc-133">1</span></span>|<span data-ttu-id="1facc-134">0</span><span class="sxs-lookup"><span data-stu-id="1facc-134">0</span></span>|  
|<span data-ttu-id="1facc-135">0</span><span class="sxs-lookup"><span data-stu-id="1facc-135">0</span></span>|<span data-ttu-id="1facc-136">0</span><span class="sxs-lookup"><span data-stu-id="1facc-136">0</span></span>|<span data-ttu-id="1facc-137">0</span><span class="sxs-lookup"><span data-stu-id="1facc-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1facc-138">Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách k zajištění přesné výsledky.</span><span class="sxs-lookup"><span data-stu-id="1facc-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="1facc-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="1facc-139">Data Types</span></span>  
 <span data-ttu-id="1facc-140">Pokud operandy se skládá z jedné `Boolean` výraz a jeden číselný výraz jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provádí logické bitové operace.</span><span class="sxs-lookup"><span data-stu-id="1facc-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="1facc-141">Logická porovnání, datový typ výsledku je `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1facc-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="1facc-142">Bitové porovnání, datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="1facc-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1facc-143">Viz tabulka "Relační a bitový operátor porovnání" [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="1facc-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1facc-144">`And` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="1facc-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1facc-145">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="1facc-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1facc-146">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1facc-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1facc-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="1facc-147">Example</span></span>  
 <span data-ttu-id="1facc-148">V následujícím příkladu `And` operátor logickou konjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="1facc-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="1facc-149">Výsledkem je `Boolean` hodnotu, která udává, zda jsou oba výrazy `True`.</span><span class="sxs-lookup"><span data-stu-id="1facc-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="1facc-150">Předchozí příklad vytváří výsledky `True` a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1facc-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1facc-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="1facc-151">Example</span></span>  
 <span data-ttu-id="1facc-152">V následujícím příkladu `And` operátor logickou konjunkci na jednotlivé bity dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="1facc-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="1facc-153">Pokud odpovídající bitů v operandy jsou nastaveny na 1, je nastaven bit vzoru výsledek.</span><span class="sxs-lookup"><span data-stu-id="1facc-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="1facc-154">V předchozím příkladu vytvoří výsledky 8, 2 a 0, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1facc-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1facc-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1facc-155">See also</span></span>

- [<span data-ttu-id="1facc-156">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1facc-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="1facc-157">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1facc-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1facc-158">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="1facc-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1facc-159">Operátor AndAlso</span><span class="sxs-lookup"><span data-stu-id="1facc-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="1facc-160">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1facc-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
