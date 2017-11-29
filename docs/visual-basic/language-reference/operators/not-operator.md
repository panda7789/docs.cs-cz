---
title: "Not – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac160aef7b7dc8acb8bf0211b403599692f2373c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="f1752-102">Not – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1752-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="f1752-103">Provede logickou negaci `Boolean` výrazu nebo bitovou negaci numerického výrazu.</span><span class="sxs-lookup"><span data-stu-id="f1752-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1752-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1752-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f1752-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f1752-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f1752-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f1752-106">Required.</span></span> <span data-ttu-id="f1752-107">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f1752-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="f1752-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f1752-108">Required.</span></span> <span data-ttu-id="f1752-109">Všechny `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f1752-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1752-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1752-110">Remarks</span></span>  
 <span data-ttu-id="f1752-111">Pro `Boolean` výrazy, následující tabulka popisuje, jak `result` je určen.</span><span class="sxs-lookup"><span data-stu-id="f1752-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f1752-112">Pokud `expression` je</span><span class="sxs-lookup"><span data-stu-id="f1752-112">If `expression` is</span></span>|<span data-ttu-id="f1752-113">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="f1752-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="f1752-114">Pro hodnotu numerické výrazy `Not` operátor Invertuje výběr hodnoty bit žádné číselného výrazu a nastaví odpovídající chvíli v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="f1752-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f1752-115">Pokud bit v `expression` je</span><span class="sxs-lookup"><span data-stu-id="f1752-115">If bit in `expression` is</span></span>|<span data-ttu-id="f1752-116">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="f1752-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="f1752-117">1</span><span class="sxs-lookup"><span data-stu-id="f1752-117">1</span></span>|<span data-ttu-id="f1752-118">0</span><span class="sxs-lookup"><span data-stu-id="f1752-118">0</span></span>|  
|<span data-ttu-id="f1752-119">0</span><span class="sxs-lookup"><span data-stu-id="f1752-119">0</span></span>|<span data-ttu-id="f1752-120">1</span><span class="sxs-lookup"><span data-stu-id="f1752-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f1752-121">Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách a zajišťují přesné provádění.</span><span class="sxs-lookup"><span data-stu-id="f1752-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f1752-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f1752-122">Data Types</span></span>  
 <span data-ttu-id="f1752-123">Logická negace, je datový typ výsledku `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f1752-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f1752-124">Pro bitovou negaci výsledný typ dat je stejný jako u `expression`.</span><span class="sxs-lookup"><span data-stu-id="f1752-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="f1752-125">Ale pokud je výraz `Decimal`, výsledkem je `Long`.</span><span class="sxs-lookup"><span data-stu-id="f1752-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f1752-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="f1752-126">Overloading</span></span>  
 <span data-ttu-id="f1752-127">`Not` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při jeho operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="f1752-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="f1752-128">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="f1752-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f1752-129">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f1752-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1752-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1752-130">Example</span></span>  
 <span data-ttu-id="f1752-131">Následující příklad používá `Not` operátor k plnění Logická negace `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="f1752-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="f1752-132">Výsledkem je, `Boolean` hodnotu, která představuje zpětného hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="f1752-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 <span data-ttu-id="f1752-133">V předchozím příkladu vytvoří výsledky `False` a `True`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f1752-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1752-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1752-134">Example</span></span>  
 <span data-ttu-id="f1752-135">Následující příklad používá `Not` operátor provést Logická negace jednotlivých bitů číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f1752-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="f1752-136">Bit ve vzoru výsledek nastaven na naopak odpovídající bit ve vzoru operand, včetně bit přihlášení.</span><span class="sxs-lookup"><span data-stu-id="f1752-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 <span data-ttu-id="f1752-137">V předchozím příkladu vytvoří výsledky –11, –9 a –7, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f1752-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1752-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1752-138">See Also</span></span>  
 [<span data-ttu-id="f1752-139">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1752-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="f1752-140">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1752-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="f1752-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="f1752-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="f1752-142">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1752-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
