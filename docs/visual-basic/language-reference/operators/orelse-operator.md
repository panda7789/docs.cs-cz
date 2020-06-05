---
title: OrElse – operátor
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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401404"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="d97bc-102">OrElse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d97bc-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="d97bc-103">Provádí krátkodobé rozvodu zahrnující logickou disjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="d97bc-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d97bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d97bc-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="d97bc-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d97bc-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d97bc-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d97bc-106">Required.</span></span> <span data-ttu-id="d97bc-107">Libovolný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="d97bc-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="d97bc-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d97bc-108">Required.</span></span> <span data-ttu-id="d97bc-109">Libovolný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="d97bc-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="d97bc-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d97bc-110">Required.</span></span> <span data-ttu-id="d97bc-111">Libovolný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="d97bc-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d97bc-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d97bc-112">Remarks</span></span>  
 <span data-ttu-id="d97bc-113">Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="d97bc-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="d97bc-114">Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="d97bc-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="d97bc-115">Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.</span><span class="sxs-lookup"><span data-stu-id="d97bc-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="d97bc-116">Pokud se oba výrazy vyhodnotí jako `True` , `result` je `True` .</span><span class="sxs-lookup"><span data-stu-id="d97bc-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="d97bc-117">Následující tabulka ukazuje, jak `result` je určena.</span><span class="sxs-lookup"><span data-stu-id="d97bc-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="d97bc-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="d97bc-118">If `expression1` is</span></span>|<span data-ttu-id="d97bc-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="d97bc-119">And `expression2` is</span></span>|<span data-ttu-id="d97bc-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="d97bc-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="d97bc-121">(nehodnoceno)</span><span class="sxs-lookup"><span data-stu-id="d97bc-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="d97bc-122">Typy dat</span><span class="sxs-lookup"><span data-stu-id="d97bc-122">Data Types</span></span>  
 <span data-ttu-id="d97bc-123">`OrElse`Operátor je definován pouze pro [datový typ Boolean](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d97bc-123">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="d97bc-124">Visual Basic každou operand podle potřeby převede `Boolean` před vyhodnocením výrazu.</span><span class="sxs-lookup"><span data-stu-id="d97bc-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="d97bc-125">Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ, který `False` se změní `0` a `True` bude se jednat o `-1` .</span><span class="sxs-lookup"><span data-stu-id="d97bc-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="d97bc-126">Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="d97bc-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="d97bc-127">Přetížení</span><span class="sxs-lookup"><span data-stu-id="d97bc-127">Overloading</span></span>  
 <span data-ttu-id="d97bc-128">[Operátor OR](or-operator.md) a operátor " [true](istrue-operator.md) " mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="d97bc-128">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d97bc-129">Přetížení operátorů `Or` a `IsTrue` ovlivňuje chování `OrElse` operátoru.</span><span class="sxs-lookup"><span data-stu-id="d97bc-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="d97bc-130">Pokud váš kód používá `OrElse` třídu nebo strukturu, která je přetížena `Or` a, ujistěte se, že `IsTrue` rozumíte jejich předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="d97bc-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="d97bc-131">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d97bc-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d97bc-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d97bc-132">Example</span></span>  
 <span data-ttu-id="d97bc-133">Následující příklad používá `OrElse` operátor k provedení logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="d97bc-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="d97bc-134">Výsledkem je `Boolean` hodnota, která představuje, zda je jeden z obou výrazů pravdivý.</span><span class="sxs-lookup"><span data-stu-id="d97bc-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="d97bc-135">Pokud je první výraz `True` , druhý není vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="d97bc-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="d97bc-136">Předchozí příklad vytvoří výsledky `True` , `True` a `False` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d97bc-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="d97bc-137">Při výpočtu není `firstCheck` druhý výraz vyhodnocen, protože první je již `True` .</span><span class="sxs-lookup"><span data-stu-id="d97bc-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="d97bc-138">Nicméně druhý výraz je vyhodnocen při výpočtu `secondCheck` .</span><span class="sxs-lookup"><span data-stu-id="d97bc-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d97bc-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d97bc-139">Example</span></span>  
 <span data-ttu-id="d97bc-140">Následující příklad ukazuje `If` příkaz... `Then` obsahující dvě volání procedur.</span><span class="sxs-lookup"><span data-stu-id="d97bc-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="d97bc-141">Pokud se první volání vrátí `True` , druhá procedura není volána.</span><span class="sxs-lookup"><span data-stu-id="d97bc-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="d97bc-142">To může vést k neočekávaným výsledkům, pokud druhý postup provádí důležité úkoly, které by měly být vždy provedeny při spuštění této části kódu.</span><span class="sxs-lookup"><span data-stu-id="d97bc-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d97bc-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d97bc-143">See also</span></span>

- [<span data-ttu-id="d97bc-144">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d97bc-144">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="d97bc-145">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d97bc-145">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d97bc-146">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="d97bc-146">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d97bc-147">Or – operátor</span><span class="sxs-lookup"><span data-stu-id="d97bc-147">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="d97bc-148">IsTrue – operátor</span><span class="sxs-lookup"><span data-stu-id="d97bc-148">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="d97bc-149">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d97bc-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
