---
title: AndAlso – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371931"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="0cc61-102">AndAlso – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cc61-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="0cc61-103">Provede krátkodobé rozvodu logického spojení na dvou výrazech.</span><span class="sxs-lookup"><span data-stu-id="0cc61-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cc61-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0cc61-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0cc61-105">Parts</span></span>  
  
|<span data-ttu-id="0cc61-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="0cc61-106">Term</span></span>|<span data-ttu-id="0cc61-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0cc61-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="0cc61-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0cc61-108">Required.</span></span> <span data-ttu-id="0cc61-109">Libovolný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="0cc61-109">Any `Boolean` expression.</span></span> <span data-ttu-id="0cc61-110">Výsledkem je `Boolean` výsledek porovnání dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="0cc61-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="0cc61-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0cc61-111">Required.</span></span> <span data-ttu-id="0cc61-112">Libovolný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="0cc61-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="0cc61-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0cc61-113">Required.</span></span> <span data-ttu-id="0cc61-114">Libovolný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="0cc61-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cc61-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cc61-115">Remarks</span></span>  
 <span data-ttu-id="0cc61-116">Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0cc61-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="0cc61-117">Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="0cc61-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="0cc61-118">Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.</span><span class="sxs-lookup"><span data-stu-id="0cc61-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="0cc61-119">Pokud se oba výrazy vyhodnotí jako `True` , `result` je `True` .</span><span class="sxs-lookup"><span data-stu-id="0cc61-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="0cc61-120">Následující tabulka ukazuje, jak `result` je určena.</span><span class="sxs-lookup"><span data-stu-id="0cc61-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0cc61-121">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="0cc61-121">If `expression1` is</span></span>|<span data-ttu-id="0cc61-122">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="0cc61-122">And `expression2` is</span></span>|<span data-ttu-id="0cc61-123">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="0cc61-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="0cc61-124">(nehodnoceno)</span><span class="sxs-lookup"><span data-stu-id="0cc61-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="0cc61-125">Typy dat</span><span class="sxs-lookup"><span data-stu-id="0cc61-125">Data Types</span></span>  
 <span data-ttu-id="0cc61-126">`AndAlso`Operátor je definován pouze pro [datový typ Boolean](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0cc61-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="0cc61-127">Visual Basic každou operand podle potřeby převede `Boolean` před vyhodnocením výrazu.</span><span class="sxs-lookup"><span data-stu-id="0cc61-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="0cc61-128">Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ, který `False` se změní `0` a `True` bude se jednat o `-1` .</span><span class="sxs-lookup"><span data-stu-id="0cc61-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="0cc61-129">Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="0cc61-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="0cc61-130">Přetížení</span><span class="sxs-lookup"><span data-stu-id="0cc61-130">Overloading</span></span>  
 <span data-ttu-id="0cc61-131">[Operátor and](and-operator.md) a operátor s hodnotou [false](isfalse-operator.md) mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0cc61-131">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0cc61-132">Přetížení operátorů `And` a `IsFalse` ovlivňuje chování `AndAlso` operátoru.</span><span class="sxs-lookup"><span data-stu-id="0cc61-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="0cc61-133">Pokud váš kód používá `AndAlso` třídu nebo strukturu, která je přetížena `And` a, ujistěte se, že `IsFalse` rozumíte jejich předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="0cc61-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="0cc61-134">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0cc61-134">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc61-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cc61-135">Example</span></span>  
 <span data-ttu-id="0cc61-136">Následující příklad používá `AndAlso` operátor k provedení logického spojení se dvěma výrazy.</span><span class="sxs-lookup"><span data-stu-id="0cc61-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="0cc61-137">Výsledkem je `Boolean` hodnota, která představuje, zda je úplný výraz JOIN pravdivý.</span><span class="sxs-lookup"><span data-stu-id="0cc61-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="0cc61-138">Pokud je první výraz `False` , druhý není vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="0cc61-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="0cc61-139">Předchozí příklad vytvoří výsledky `True` , a v `False` `False` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0cc61-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="0cc61-140">Při výpočtu není `secondCheck` druhý výraz vyhodnocen, protože první je již `False` .</span><span class="sxs-lookup"><span data-stu-id="0cc61-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="0cc61-141">Nicméně druhý výraz je vyhodnocen při výpočtu `thirdCheck` .</span><span class="sxs-lookup"><span data-stu-id="0cc61-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc61-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cc61-142">Example</span></span>  
 <span data-ttu-id="0cc61-143">Následující příklad ukazuje `Function` proceduru, která vyhledává danou hodnotu mezi prvky pole.</span><span class="sxs-lookup"><span data-stu-id="0cc61-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="0cc61-144">Pokud je pole prázdné nebo pokud byla překročena délka pole, `While` příkaz netestuje prvek pole proti hledané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="0cc61-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="0cc61-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cc61-145">See also</span></span>

- [<span data-ttu-id="0cc61-146">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cc61-146">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="0cc61-147">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cc61-147">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0cc61-148">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0cc61-148">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0cc61-149">And – operátor</span><span class="sxs-lookup"><span data-stu-id="0cc61-149">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="0cc61-150">IsFalse – operátor</span><span class="sxs-lookup"><span data-stu-id="0cc61-150">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="0cc61-151">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cc61-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
