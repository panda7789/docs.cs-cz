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
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860145"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="4e380-102">OrElse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e380-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="4e380-103">Provede zkrácenou inkluzivní logickou disjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="4e380-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e380-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e380-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="4e380-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4e380-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="4e380-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4e380-106">Required.</span></span> <span data-ttu-id="4e380-107">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e380-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="4e380-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4e380-108">Required.</span></span> <span data-ttu-id="4e380-109">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e380-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="4e380-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4e380-110">Required.</span></span> <span data-ttu-id="4e380-111">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e380-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e380-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e380-112">Remarks</span></span>  
 <span data-ttu-id="4e380-113">Logické operace se říká, že *zkrácenou* Pokud zkompilovaný kód může obejít vyhodnocení výrazů v závislosti na výsledek jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="4e380-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="4e380-114">Pokud výsledek první výraz vyhodnotí Určuje konečný výsledek operace, není nutné k vyhodnocení, druhý výraz, protože jej nelze změnit na konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="4e380-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="4e380-115">Krátký cyklus může zlepšit výkon, pokud jednorázovým přihlášením výrazu je komplexní nebo zahrnuje volání procedur.</span><span class="sxs-lookup"><span data-stu-id="4e380-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="4e380-116">Pokud mají jednoho nebo obou výrazech `True`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="4e380-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="4e380-117">Následující tabulka ukazuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="4e380-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="4e380-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="4e380-118">If `expression1` is</span></span>|<span data-ttu-id="4e380-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="4e380-119">And `expression2` is</span></span>|<span data-ttu-id="4e380-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="4e380-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="4e380-121">(nevyhodnoceno)</span><span class="sxs-lookup"><span data-stu-id="4e380-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="4e380-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4e380-122">Data Types</span></span>  
 <span data-ttu-id="4e380-123">`OrElse` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4e380-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="4e380-124">Visual Basic převede operandem tak, aby `Boolean` před vyhodnocením výrazu.</span><span class="sxs-lookup"><span data-stu-id="4e380-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="4e380-125">Pokud přiřadíte číselného typu výsledku, ho z Visual Basic převede `Boolean` k danému typu tak, aby `False` stane `0` a `True` stane `-1`.</span><span class="sxs-lookup"><span data-stu-id="4e380-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="4e380-126">Další informace najdete v tématu [logická převody typu](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="4e380-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="4e380-127">Přetížení</span><span class="sxs-lookup"><span data-stu-id="4e380-127">Overloading</span></span>  
 <span data-ttu-id="4e380-128">[Nebo operátor](../../../visual-basic/language-reference/operators/or-operator.md) a [IsTrue operátor](../../../visual-basic/language-reference/operators/istrue-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="4e380-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4e380-129">Přetížení `Or` a `IsTrue` operátory má vliv na chování `OrElse` operátor.</span><span class="sxs-lookup"><span data-stu-id="4e380-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="4e380-130">Pokud váš kód používá `OrElse` v třídě nebo struktuře, která přetížení `Or` a `IsTrue`, je nutné pochopit jejich Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="4e380-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="4e380-131">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4e380-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e380-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e380-132">Example</span></span>  
 <span data-ttu-id="4e380-133">V následujícím příkladu `OrElse` operátor provádět logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="4e380-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="4e380-134">Výsledkem je `Boolean` hodnotu, která udává, zda je splněna jedna ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="4e380-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="4e380-135">Pokud je první výraz `True`, druhý se už nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="4e380-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="4e380-136">Předchozí příklad vytváří výsledky `True`, `True`, a `False` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4e380-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="4e380-137">Při výpočtu `firstCheck`, druhý výraz není vyhodnocen, protože první je již `True`.</span><span class="sxs-lookup"><span data-stu-id="4e380-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="4e380-138">Nicméně, druhý výraz je vyhodnocen při výpočtu `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="4e380-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e380-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e380-139">Example</span></span>  
 <span data-ttu-id="4e380-140">Následující příklad ukazuje `If`... `Then` příkazu, který obsahuje dvě volání procedur.</span><span class="sxs-lookup"><span data-stu-id="4e380-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="4e380-141">Pokud první volání vrátí `True`, druhý postup není volána.</span><span class="sxs-lookup"><span data-stu-id="4e380-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="4e380-142">Pokud se druhý postup provádí důležité úkoly, které mají být provedeny vždy při spuštění této části kódu, může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="4e380-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="4e380-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e380-143">See also</span></span>

- [<span data-ttu-id="4e380-144">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e380-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="4e380-145">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e380-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4e380-146">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="4e380-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4e380-147">Operátor Or</span><span class="sxs-lookup"><span data-stu-id="4e380-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="4e380-148">Operátor IsTrue</span><span class="sxs-lookup"><span data-stu-id="4e380-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="4e380-149">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e380-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
