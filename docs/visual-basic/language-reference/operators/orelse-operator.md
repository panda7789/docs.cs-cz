---
title: "OrElse – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47239a1d2b5b20f2b8cacc9b9185a0f95f63dc84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="b9c64-102">OrElse – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9c64-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="b9c64-103">Provede zkrácenou včetně logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9c64-104">Syntax</span></span>  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b9c64-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b9c64-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b9c64-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b9c64-106">Required.</span></span> <span data-ttu-id="b9c64-107">Všechny `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="b9c64-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="b9c64-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b9c64-108">Required.</span></span> <span data-ttu-id="b9c64-109">Všechny `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="b9c64-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b9c64-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b9c64-110">Required.</span></span> <span data-ttu-id="b9c64-111">Všechny `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="b9c64-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9c64-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9c64-112">Remarks</span></span>  
 <span data-ttu-id="b9c64-113">Logický provoz se říká, že *krátká smyčka* Pokud zkompilovaný kód můžete vynechat vyhodnocení jeden výraz v závislosti na výsledku další výraz.</span><span class="sxs-lookup"><span data-stu-id="b9c64-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="b9c64-114">Pokud výsledek první výrazu vyhodnoceného Určuje konečný výsledek operace, není třeba vyhodnotit druhý výraz, protože jej nelze změnit konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="b9c64-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="b9c64-115">Krátká smyčka může zlepšit výkon, pokud přeskočených výrazu je složité, nebo pokud se týká volání procedur.</span><span class="sxs-lookup"><span data-stu-id="b9c64-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="b9c64-116">Pokud nebo oba výrazy vyhodnocení `True`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="b9c64-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="b9c64-117">Následující tabulka popisuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="b9c64-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="b9c64-118">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="b9c64-118">If `expression1` is</span></span>|<span data-ttu-id="b9c64-119">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="b9c64-119">And `expression2` is</span></span>|<span data-ttu-id="b9c64-120">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="b9c64-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="b9c64-121">(není vyhodnotit)</span><span class="sxs-lookup"><span data-stu-id="b9c64-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="b9c64-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b9c64-122">Data Types</span></span>  
 <span data-ttu-id="b9c64-123">`OrElse` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b9c64-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="b9c64-124">Visual Basic převede každý operand podle potřeby k `Boolean` a provede operaci zcela v `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b9c64-124">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="b9c64-125">Chcete-li přiřadit výsledek na číselný typ, Visual Basic převede z `Boolean` do daného typu.</span><span class="sxs-lookup"><span data-stu-id="b9c64-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="b9c64-126">To by mohla vést k neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="b9c64-126">This could produce unexpected behavior.</span></span> <span data-ttu-id="b9c64-127">Například `5 OrElse 12` výsledkem `–1` při převodu do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b9c64-127">For example, `5 OrElse 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b9c64-128">Přetížení</span><span class="sxs-lookup"><span data-stu-id="b9c64-128">Overloading</span></span>  
 <span data-ttu-id="b9c64-129">[Operátor nebo](../../../visual-basic/language-reference/operators/or-operator.md) a [IsTrue – operátor](../../../visual-basic/language-reference/operators/istrue-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat jejich chování při operand má typ této třídy nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="b9c64-129">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b9c64-130">Přetížení `Or` a `IsTrue` operátory má vliv na chování `OrElse` operátor.</span><span class="sxs-lookup"><span data-stu-id="b9c64-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="b9c64-131">Pokud váš kód používá `OrElse` na třídu nebo strukturu, která přetížení `Or` a `IsTrue`, ujistěte se, rozumíte jejich Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="b9c64-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="b9c64-132">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b9c64-132">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c64-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9c64-133">Example</span></span>  
 <span data-ttu-id="b9c64-134">Následující příklad používá `OrElse` operátor provést logické disjunkce dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="b9c64-135">Výsledkem je, `Boolean` hodnotu, která představuje zda je splněna jedna ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="b9c64-136">Pokud je první výraz `True`, druhá, nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="b9c64-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 <span data-ttu-id="b9c64-137">V předchozím příkladu vytvoří výsledky `True`, `True`, a `False` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b9c64-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="b9c64-138">Při výpočtu `firstCheck`, druhý výraz není vyhodnotit, protože první je již `True`.</span><span class="sxs-lookup"><span data-stu-id="b9c64-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="b9c64-139">Ale druhý výraz vyhodnotí při výpočtu `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="b9c64-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c64-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9c64-140">Example</span></span>  
 <span data-ttu-id="b9c64-141">Následující příklad ukazuje `If`... `Then` příkazu, který obsahuje dva volání procedur.</span><span class="sxs-lookup"><span data-stu-id="b9c64-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="b9c64-142">Pokud vrátí první volání `True`, druhý postup není volán.</span><span class="sxs-lookup"><span data-stu-id="b9c64-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="b9c64-143">Pokud se druhý postup provádí důležité úlohy, které mají být provedeny vždy při spuštění této části kódu, může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="b9c64-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b9c64-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9c64-144">See Also</span></span>  
 [<span data-ttu-id="b9c64-145">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9c64-145">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="b9c64-146">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9c64-146">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b9c64-147">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b9c64-147">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b9c64-148">Or – operátor</span><span class="sxs-lookup"><span data-stu-id="b9c64-148">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)  
 [<span data-ttu-id="b9c64-149">IsTrue – operátor</span><span class="sxs-lookup"><span data-stu-id="b9c64-149">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="b9c64-150">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9c64-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
