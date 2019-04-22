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
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835294"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="f9dc0-102">Or – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9dc0-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="f9dc0-103">Provede logickou disjunkci dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9dc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9dc0-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f9dc0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f9dc0-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f9dc0-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-106">Required.</span></span> <span data-ttu-id="f9dc0-107">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="f9dc0-108">Pro `Boolean` porovnání, `result` je inkluzivní logickou disjunkci dvou `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="f9dc0-109">Pro bitové operace `result` číselná hodnota představující včetně bitovou disjunkci dvou číselných bitové vzory.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f9dc0-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-110">Required.</span></span> <span data-ttu-id="f9dc0-111">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f9dc0-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-112">Required.</span></span> <span data-ttu-id="f9dc0-113">Žádné `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9dc0-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9dc0-114">Remarks</span></span>  
 <span data-ttu-id="f9dc0-115">Pro `Boolean` porovnání, `result` je `False` Pokud a pouze pokud oba `expression1` a `expression2` vyhodnotit `False`.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="f9dc0-116">Následující tabulka ukazuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f9dc0-117">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="f9dc0-117">If `expression1` is</span></span>|<span data-ttu-id="f9dc0-118">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="f9dc0-118">And `expression2` is</span></span>|<span data-ttu-id="f9dc0-119">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="f9dc0-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="f9dc0-120">V `Boolean` porovnání, `Or` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="f9dc0-121">[OrElse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md) provádí *zkrácenou*, což znamená, že pokud `expression1` je `True`, pak `expression2` , nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="f9dc0-122">Pro bitové operace `Or` operátor provádí porovnání bitového stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající bit v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f9dc0-123">Pokud bit v `expression1` je</span><span class="sxs-lookup"><span data-stu-id="f9dc0-123">If bit in `expression1` is</span></span>|<span data-ttu-id="f9dc0-124">A bitu v `expression2` je</span><span class="sxs-lookup"><span data-stu-id="f9dc0-124">And bit in `expression2` is</span></span>|<span data-ttu-id="f9dc0-125">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="f9dc0-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="f9dc0-126">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-126">1</span></span>|<span data-ttu-id="f9dc0-127">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-127">1</span></span>|<span data-ttu-id="f9dc0-128">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-128">1</span></span>|  
|<span data-ttu-id="f9dc0-129">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-129">1</span></span>|<span data-ttu-id="f9dc0-130">0</span><span class="sxs-lookup"><span data-stu-id="f9dc0-130">0</span></span>|<span data-ttu-id="f9dc0-131">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-131">1</span></span>|  
|<span data-ttu-id="f9dc0-132">0</span><span class="sxs-lookup"><span data-stu-id="f9dc0-132">0</span></span>|<span data-ttu-id="f9dc0-133">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-133">1</span></span>|<span data-ttu-id="f9dc0-134">1</span><span class="sxs-lookup"><span data-stu-id="f9dc0-134">1</span></span>|  
|<span data-ttu-id="f9dc0-135">0</span><span class="sxs-lookup"><span data-stu-id="f9dc0-135">0</span></span>|<span data-ttu-id="f9dc0-136">0</span><span class="sxs-lookup"><span data-stu-id="f9dc0-136">0</span></span>|<span data-ttu-id="f9dc0-137">0</span><span class="sxs-lookup"><span data-stu-id="f9dc0-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f9dc0-138">Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách zajistit správné spuštění.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f9dc0-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f9dc0-139">Data Types</span></span>  
 <span data-ttu-id="f9dc0-140">Pokud operandy se skládá z jedné `Boolean` výraz a jeden číselný výraz jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provádí logické bitové operace.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="f9dc0-141">Pro `Boolean` porovnání, datový typ výsledku je `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f9dc0-142">Bitové porovnání, datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="f9dc0-143">Viz tabulka "Relační a bitový operátor porovnání" [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="f9dc0-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f9dc0-144">Přetížení</span><span class="sxs-lookup"><span data-stu-id="f9dc0-144">Overloading</span></span>  
 <span data-ttu-id="f9dc0-145">`Or` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f9dc0-146">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f9dc0-147">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f9dc0-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dc0-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9dc0-148">Example</span></span>  
 <span data-ttu-id="f9dc0-149">V následujícím příkladu `Or` operátor inkluzivní logickou disjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="f9dc0-150">Výsledkem je `Boolean` hodnotu, která udává, zda je jedna ze dvou výrazů `True`.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="f9dc0-151">Předchozí příklad vytváří výsledky `True`, `True`, a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dc0-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9dc0-152">Example</span></span>  
 <span data-ttu-id="f9dc0-153">V následujícím příkladu `Or` operátor inkluzivní logickou disjunkci na jednotlivé bity dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="f9dc0-154">Pokud některý z odpovídající bitů v operandů je nastavená na 1, je nastaven bit vzoru výsledek.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="f9dc0-155">V předchozím příkladu vytvoří výsledky 10, 14 a 14, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f9dc0-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dc0-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9dc0-156">See also</span></span>

- [<span data-ttu-id="f9dc0-157">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9dc0-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="f9dc0-158">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9dc0-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f9dc0-159">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="f9dc0-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f9dc0-160">Operátor OrElse</span><span class="sxs-lookup"><span data-stu-id="f9dc0-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="f9dc0-161">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9dc0-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
