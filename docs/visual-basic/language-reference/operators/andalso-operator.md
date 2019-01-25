---
title: AndAlso – operátor (Visual Basic)
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
ms.openlocfilehash: c9f4d9c880e189eb0ad4834736bdc664eb5b4376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703559"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="e9d1c-102">AndAlso – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9d1c-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="e9d1c-103">Provede zkrácenou logickou konjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9d1c-104">Syntax</span></span>  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e9d1c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e9d1c-105">Parts</span></span>  
  
|<span data-ttu-id="e9d1c-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e9d1c-106">Term</span></span>|<span data-ttu-id="e9d1c-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e9d1c-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="e9d1c-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-108">Required.</span></span> <span data-ttu-id="e9d1c-109">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-109">Any `Boolean` expression.</span></span> <span data-ttu-id="e9d1c-110">Výsledkem je, `Boolean` výsledku porovnání řetězců dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="e9d1c-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-111">Required.</span></span> <span data-ttu-id="e9d1c-112">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="e9d1c-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-113">Required.</span></span> <span data-ttu-id="e9d1c-114">Žádné `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9d1c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9d1c-115">Remarks</span></span>  
 <span data-ttu-id="e9d1c-116">Logické operace se říká, že *zkrácenou* Pokud zkompilovaný kód může obejít vyhodnocení výrazů v závislosti na výsledek jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="e9d1c-117">Pokud výsledek první výraz vyhodnotí Určuje konečný výsledek operace, není nutné k vyhodnocení, druhý výraz, protože jej nelze změnit na konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="e9d1c-118">Krátký cyklus může zlepšit výkon, pokud jednorázovým přihlášením výrazu je komplexní nebo zahrnuje volání procedur.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="e9d1c-119">Pokud mají oba výrazy `True`, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="e9d1c-120">Následující tabulka ukazuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="e9d1c-121">Pokud `expression1` je</span><span class="sxs-lookup"><span data-stu-id="e9d1c-121">If `expression1` is</span></span>|<span data-ttu-id="e9d1c-122">A `expression2` je</span><span class="sxs-lookup"><span data-stu-id="e9d1c-122">And `expression2` is</span></span>|<span data-ttu-id="e9d1c-123">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="e9d1c-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="e9d1c-124">(nevyhodnoceno)</span><span class="sxs-lookup"><span data-stu-id="e9d1c-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="e9d1c-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e9d1c-125">Data Types</span></span>  
 <span data-ttu-id="e9d1c-126">`AndAlso` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e9d1c-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="e9d1c-127">Visual Basic převede operandem tak, aby `Boolean` a provádí operaci, která je zcela v `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-127">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="e9d1c-128">Pokud přiřadíte číselného typu výsledku, ho z Visual Basic převede `Boolean` k danému typu.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="e9d1c-129">To by mohla vést k neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-129">This could produce unexpected behavior.</span></span> <span data-ttu-id="e9d1c-130">Například `5 AndAlso 12` výsledkem `–1` při převodu na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-130">For example, `5 AndAlso 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e9d1c-131">Přetížení</span><span class="sxs-lookup"><span data-stu-id="e9d1c-131">Overloading</span></span>  
 <span data-ttu-id="e9d1c-132">[Operátoru](../../../visual-basic/language-reference/operators/and-operator.md) a [IsFalse operátor](../../../visual-basic/language-reference/operators/isfalse-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ, který třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-132">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e9d1c-133">Přetížení `And` a `IsFalse` operátory má vliv na chování `AndAlso` operátor.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="e9d1c-134">Pokud váš kód používá `AndAlso` v třídě nebo struktuře, která přetížení `And` a `IsFalse`, je nutné pochopit jejich Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="e9d1c-135">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e9d1c-135">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9d1c-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9d1c-136">Example</span></span>  
 <span data-ttu-id="e9d1c-137">V následujícím příkladu `AndAlso` operátor logickou konjunkci dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="e9d1c-138">Výsledkem je `Boolean` , která udává, zda conjoined celý výraz hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="e9d1c-139">Pokud je první výraz `False`, druhý se už nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 <span data-ttu-id="e9d1c-140">Předchozí příklad vytváří výsledky `True`, `False`, a `False`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="e9d1c-141">Při výpočtu `secondCheck`, druhý výraz není vyhodnocen, protože první je již `False`.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="e9d1c-142">Nicméně, druhý výraz je vyhodnocen při výpočtu `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9d1c-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9d1c-143">Example</span></span>  
 <span data-ttu-id="e9d1c-144">Následující příklad ukazuje `Function` proceduru, která hledá pro danou hodnotu mezi prvky pole.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="e9d1c-145">Pokud je pole prázdné, nebo pokud byla překročena délka pole, `While` příkaz netestuje na prvek pole s hodnotou vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="e9d1c-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9d1c-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9d1c-146">See also</span></span>
- [<span data-ttu-id="e9d1c-147">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9d1c-147">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="e9d1c-148">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9d1c-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e9d1c-149">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="e9d1c-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e9d1c-150">Operátor And</span><span class="sxs-lookup"><span data-stu-id="e9d1c-150">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="e9d1c-151">Operátor IsFalse</span><span class="sxs-lookup"><span data-stu-id="e9d1c-151">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="e9d1c-152">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9d1c-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
