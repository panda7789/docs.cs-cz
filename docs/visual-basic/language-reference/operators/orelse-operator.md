---
title: OrElse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835235"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="d4b52-102">OrElse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b52-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="d4b52-103">Provádí krátkodobé rozvodu zahrnující logickou disjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="d4b52-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b52-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="d4b52-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d4b52-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d4b52-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d4b52-106">Required.</span></span> <span data-ttu-id="d4b52-107">Libovolný výraz `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="d4b52-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d4b52-108">Required.</span></span> <span data-ttu-id="d4b52-109">Libovolný výraz `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="d4b52-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d4b52-110">Required.</span></span> <span data-ttu-id="d4b52-111">Libovolný výraz `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4b52-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4b52-112">Remarks</span></span>  
 <span data-ttu-id="d4b52-113">Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="d4b52-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="d4b52-114">Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="d4b52-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="d4b52-115">Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.</span><span class="sxs-lookup"><span data-stu-id="d4b52-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="d4b52-116">Pokud se jeden nebo oba výrazy vyhodnotí jako `True`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="d4b52-117">Následující tabulka ukazuje, jak je určena `result`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="d4b52-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="d4b52-118">If `expression1` is</span></span>|<span data-ttu-id="d4b52-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="d4b52-119">And `expression2` is</span></span>|<span data-ttu-id="d4b52-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="d4b52-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="d4b52-121">(nehodnoceno)</span><span class="sxs-lookup"><span data-stu-id="d4b52-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="d4b52-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="d4b52-122">Data Types</span></span>  
 <span data-ttu-id="d4b52-123">Operátor `OrElse` je definován pouze pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d4b52-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="d4b52-124">Visual Basic převede každý operand podle potřeby, aby `Boolean` před vyhodnocením výrazu.</span><span class="sxs-lookup"><span data-stu-id="d4b52-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="d4b52-125">Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ tak, aby `False` se staly `0` a `True` se `-1`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="d4b52-126">Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="d4b52-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="d4b52-127">Přetížení</span><span class="sxs-lookup"><span data-stu-id="d4b52-127">Overloading</span></span>  
 <span data-ttu-id="d4b52-128">[Operátor OR](../../../visual-basic/language-reference/operators/or-operator.md) a operátor " [true](../../../visual-basic/language-reference/operators/istrue-operator.md) " mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="d4b52-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d4b52-129">Přetížení operátorů `Or` a `IsTrue` má vliv na chování operátoru `OrElse`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="d4b52-130">Pokud váš kód používá `OrElse` u třídy nebo struktury, která přetěžuje `Or` a `IsTrue`, ujistěte se, že rozumíte jejich předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="d4b52-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="d4b52-131">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d4b52-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4b52-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4b52-132">Example</span></span>  
 <span data-ttu-id="d4b52-133">Následující příklad používá operátor `OrElse` k provedení logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="d4b52-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="d4b52-134">Výsledkem je hodnota @no__t 0, která představuje, zda jsou oba výrazy pravdivé.</span><span class="sxs-lookup"><span data-stu-id="d4b52-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="d4b52-135">Pokud je první výraz `True`, druhý se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="d4b52-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="d4b52-136">Předchozí příklad vytvoří výsledky `True`, `True` a @no__t – 2.</span><span class="sxs-lookup"><span data-stu-id="d4b52-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="d4b52-137">Při výpočtu `firstCheck` není druhý výraz vyhodnocen, protože první je již `True`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="d4b52-138">Nicméně druhý výraz je vyhodnocen při výpočtu `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="d4b52-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4b52-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4b52-139">Example</span></span>  
 <span data-ttu-id="d4b52-140">Následující příklad ukazuje příkaz `If`... `Then` obsahující dvě volání procedur.</span><span class="sxs-lookup"><span data-stu-id="d4b52-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="d4b52-141">Pokud první volání vrátí `True`, druhá procedura není volána.</span><span class="sxs-lookup"><span data-stu-id="d4b52-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="d4b52-142">To může vést k neočekávaným výsledkům, pokud druhý postup provádí důležité úkoly, které by měly být vždy provedeny při spuštění této části kódu.</span><span class="sxs-lookup"><span data-stu-id="d4b52-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d4b52-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4b52-143">See also</span></span>

- [<span data-ttu-id="d4b52-144">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b52-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="d4b52-145">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4b52-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d4b52-146">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="d4b52-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d4b52-147">Operátor Or</span><span class="sxs-lookup"><span data-stu-id="d4b52-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="d4b52-148">Operátor IsTrue</span><span class="sxs-lookup"><span data-stu-id="d4b52-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="d4b52-149">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4b52-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
