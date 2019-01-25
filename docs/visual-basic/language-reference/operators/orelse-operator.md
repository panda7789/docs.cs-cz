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
ms.openlocfilehash: 70bbfef54d3f716e0e7463a39ee15e8480066695
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603011"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="93b1e-102">OrElse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93b1e-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="93b1e-103">Provede zkrácenou inkluzivní logickou disjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="93b1e-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93b1e-104">Syntax</span></span>  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="93b1e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="93b1e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="93b1e-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="93b1e-106">Required.</span></span> <span data-ttu-id="93b1e-107">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="93b1e-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="93b1e-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="93b1e-108">Required.</span></span> <span data-ttu-id="93b1e-109">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="93b1e-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="93b1e-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="93b1e-110">Required.</span></span> <span data-ttu-id="93b1e-111">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="93b1e-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93b1e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93b1e-112">Remarks</span></span>  
 <span data-ttu-id="93b1e-113">Logické operace se říká, že *zkrácenou* Pokud zkompilovaný kód může obejít vyhodnocení výrazů v závislosti na výsledek jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="93b1e-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="93b1e-114">Pokud výsledek první výraz vyhodnotí Určuje konečný výsledek operace, není nutné k vyhodnocení, druhý výraz, protože jej nelze změnit na konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="93b1e-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="93b1e-115">Krátký cyklus může zlepšit výkon, pokud jednorázovým přihlášením výrazu je komplexní nebo zahrnuje volání procedur.</span><span class="sxs-lookup"><span data-stu-id="93b1e-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="93b1e-116">Pokud mají jednoho nebo obou výrazech `True`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="93b1e-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="93b1e-117">Následující tabulka ukazuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="93b1e-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="93b1e-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="93b1e-118">If `expression1` is</span></span>|<span data-ttu-id="93b1e-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="93b1e-119">And `expression2` is</span></span>|<span data-ttu-id="93b1e-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="93b1e-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="93b1e-121">(nevyhodnoceno)</span><span class="sxs-lookup"><span data-stu-id="93b1e-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="93b1e-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="93b1e-122">Data Types</span></span>  
 <span data-ttu-id="93b1e-123">`OrElse` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="93b1e-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="93b1e-124">Visual Basic převede operandem tak, aby `Boolean` a provádí operaci, která je zcela v `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="93b1e-124">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="93b1e-125">Pokud přiřadíte číselného typu výsledku, ho z Visual Basic převede `Boolean` k danému typu.</span><span class="sxs-lookup"><span data-stu-id="93b1e-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="93b1e-126">To by mohla vést k neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="93b1e-126">This could produce unexpected behavior.</span></span> <span data-ttu-id="93b1e-127">Například `5 OrElse 12` výsledkem `–1` při převodu na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="93b1e-127">For example, `5 OrElse 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="93b1e-128">Přetížení</span><span class="sxs-lookup"><span data-stu-id="93b1e-128">Overloading</span></span>  
 <span data-ttu-id="93b1e-129">[Nebo operátor](../../../visual-basic/language-reference/operators/or-operator.md) a [IsTrue operátor](../../../visual-basic/language-reference/operators/istrue-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="93b1e-129">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="93b1e-130">Přetížení `Or` a `IsTrue` operátory má vliv na chování `OrElse` operátor.</span><span class="sxs-lookup"><span data-stu-id="93b1e-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="93b1e-131">Pokud váš kód používá `OrElse` v třídě nebo struktuře, která přetížení `Or` a `IsTrue`, je nutné pochopit jejich Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="93b1e-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="93b1e-132">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="93b1e-132">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93b1e-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="93b1e-133">Example</span></span>  
 <span data-ttu-id="93b1e-134">V následujícím příkladu `OrElse` operátor provádět logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="93b1e-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="93b1e-135">Výsledkem je `Boolean` hodnotu, která udává, zda je splněna jedna ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="93b1e-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="93b1e-136">Pokud je první výraz `True`, druhý se už nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="93b1e-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 <span data-ttu-id="93b1e-137">Předchozí příklad vytváří výsledky `True`, `True`, a `False` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="93b1e-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="93b1e-138">Při výpočtu `firstCheck`, druhý výraz není vyhodnocen, protože první je již `True`.</span><span class="sxs-lookup"><span data-stu-id="93b1e-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="93b1e-139">Nicméně, druhý výraz je vyhodnocen při výpočtu `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="93b1e-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93b1e-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="93b1e-140">Example</span></span>  
 <span data-ttu-id="93b1e-141">Následující příklad ukazuje `If`... `Then` příkazu, který obsahuje dvě volání procedur.</span><span class="sxs-lookup"><span data-stu-id="93b1e-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="93b1e-142">Pokud první volání vrátí `True`, druhý postup není volána.</span><span class="sxs-lookup"><span data-stu-id="93b1e-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="93b1e-143">Pokud se druhý postup provádí důležité úkoly, které mají být provedeny vždy při spuštění této části kódu, může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="93b1e-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="93b1e-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93b1e-144">See also</span></span>
- [<span data-ttu-id="93b1e-145">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93b1e-145">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="93b1e-146">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93b1e-146">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="93b1e-147">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="93b1e-147">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="93b1e-148">Operátor Or</span><span class="sxs-lookup"><span data-stu-id="93b1e-148">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="93b1e-149">Operátor IsTrue</span><span class="sxs-lookup"><span data-stu-id="93b1e-149">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="93b1e-150">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93b1e-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
