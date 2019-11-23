---
title: Not – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
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
ms.openlocfilehash: 5ebc5f9dbf674a9a6560bd96b3e8c9edcae08a81
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701078"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="cbe0e-102">Not – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbe0e-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="cbe0e-103">Provede logickou negaci výrazu `Boolean` nebo bitovou negaci u číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbe0e-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="cbe0e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="cbe0e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="cbe0e-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-106">Required.</span></span> <span data-ttu-id="cbe0e-107">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="cbe0e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-108">Required.</span></span> <span data-ttu-id="cbe0e-109">Libovolný `Boolean` nebo číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbe0e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbe0e-110">Remarks</span></span>  
 <span data-ttu-id="cbe0e-111">V případě výrazů `Boolean` ukazuje následující tabulka způsob určení `result`.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="cbe0e-112">Pokud je `expression`</span><span class="sxs-lookup"><span data-stu-id="cbe0e-112">If `expression` is</span></span>|<span data-ttu-id="cbe0e-113">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="cbe0e-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="cbe0e-114">U numerických výrazů operátor `Not` Invertuje bitové hodnoty libovolného číselného výrazu a nastaví odpovídající bit v `result` podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="cbe0e-115">Pokud je bit v `expression`</span><span class="sxs-lookup"><span data-stu-id="cbe0e-115">If bit in `expression` is</span></span>|<span data-ttu-id="cbe0e-116">Bit ve `result` je</span><span class="sxs-lookup"><span data-stu-id="cbe0e-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="cbe0e-117">1</span><span class="sxs-lookup"><span data-stu-id="cbe0e-117">1</span></span>|<span data-ttu-id="cbe0e-118">0</span><span class="sxs-lookup"><span data-stu-id="cbe0e-118">0</span></span>|  
|<span data-ttu-id="cbe0e-119">0</span><span class="sxs-lookup"><span data-stu-id="cbe0e-119">0</span></span>|<span data-ttu-id="cbe0e-120">1</span><span class="sxs-lookup"><span data-stu-id="cbe0e-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="cbe0e-121">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="cbe0e-122">Datové typy</span><span class="sxs-lookup"><span data-stu-id="cbe0e-122">Data Types</span></span>  
 <span data-ttu-id="cbe0e-123">Pro logickou negaci je datový typ výsledku `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="cbe0e-124">Pro bitovou negaci je výsledný datový typ stejný jako u `expression`.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="cbe0e-125">Pokud je však výraz `Decimal`, výsledek je `Long`.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cbe0e-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="cbe0e-126">Overloading</span></span>  
 <span data-ttu-id="cbe0e-127">Operátor `Not` může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má jeho operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="cbe0e-128">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cbe0e-129">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cbe0e-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe0e-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbe0e-130">Example</span></span>  
 <span data-ttu-id="cbe0e-131">Následující příklad používá operátor `Not` k provedení logické negace výrazu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="cbe0e-132">Výsledkem je `Boolean` hodnota, která představuje opačnou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="cbe0e-133">Předchozí příklad vytvoří výsledky `False` a `True`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe0e-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbe0e-134">Example</span></span>  
 <span data-ttu-id="cbe0e-135">Následující příklad používá operátor `Not` k provedení logické negace jednotlivých bitů číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="cbe0e-136">Bit ve vzorci výsledků je nastaven na zpětný výsledek odpovídajícího bitu ve vzoru operandu, včetně bitu znaménka.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="cbe0e-137">Předchozí příklad vytvoří výsledky – 11, – 9 a – 7 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cbe0e-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe0e-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbe0e-138">See also</span></span>

- [<span data-ttu-id="cbe0e-139">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbe0e-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="cbe0e-140">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbe0e-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="cbe0e-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="cbe0e-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cbe0e-142">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbe0e-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
