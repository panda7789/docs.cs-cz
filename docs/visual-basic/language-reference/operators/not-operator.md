---
title: Not – operátor
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
ms.openlocfilehash: 56cdeb80a217dbce15921eddd6a43d8d1b049376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401456"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="ac9a2-102">Not – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac9a2-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="ac9a2-103">Provede logickou negaci `Boolean` výrazu nebo bitovou negaci číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac9a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac9a2-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ac9a2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ac9a2-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="ac9a2-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-106">Required.</span></span> <span data-ttu-id="ac9a2-107">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="ac9a2-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-108">Required.</span></span> <span data-ttu-id="ac9a2-109">Libovolný `Boolean` nebo numerický výraz.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac9a2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac9a2-110">Remarks</span></span>  
 <span data-ttu-id="ac9a2-111">`Boolean`V případě výrazů ukazuje následující tabulka, jak `result` je určena.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="ac9a2-112">Pokud `expression` je</span><span class="sxs-lookup"><span data-stu-id="ac9a2-112">If `expression` is</span></span>|<span data-ttu-id="ac9a2-113">Hodnota `result` je</span><span class="sxs-lookup"><span data-stu-id="ac9a2-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="ac9a2-114">U numerických výrazů `Not` operátor obrátí bitové hodnoty libovolného číselného výrazu a nastaví odpovídající bit v `result` závislosti na následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="ac9a2-115">Pokud je bit v `expression`</span><span class="sxs-lookup"><span data-stu-id="ac9a2-115">If bit in `expression` is</span></span>|<span data-ttu-id="ac9a2-116">Bit v `result` je</span><span class="sxs-lookup"><span data-stu-id="ac9a2-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="ac9a2-117">1</span><span class="sxs-lookup"><span data-stu-id="ac9a2-117">1</span></span>|<span data-ttu-id="ac9a2-118">0</span><span class="sxs-lookup"><span data-stu-id="ac9a2-118">0</span></span>|  
|<span data-ttu-id="ac9a2-119">0</span><span class="sxs-lookup"><span data-stu-id="ac9a2-119">0</span></span>|<span data-ttu-id="ac9a2-120">1</span><span class="sxs-lookup"><span data-stu-id="ac9a2-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ac9a2-121">Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="ac9a2-122">Typy dat</span><span class="sxs-lookup"><span data-stu-id="ac9a2-122">Data Types</span></span>  
 <span data-ttu-id="ac9a2-123">Pro logickou negaci je datový typ výsledku `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="ac9a2-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="ac9a2-124">Pro bitovou negaci je výsledný datový typ stejný jako u `expression` .</span><span class="sxs-lookup"><span data-stu-id="ac9a2-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="ac9a2-125">Nicméně pokud je výraz `Decimal` , je výsledkem `Long` .</span><span class="sxs-lookup"><span data-stu-id="ac9a2-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ac9a2-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="ac9a2-126">Overloading</span></span>  
 <span data-ttu-id="ac9a2-127">`Not`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="ac9a2-128">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ac9a2-129">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ac9a2-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac9a2-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac9a2-130">Example</span></span>  
 <span data-ttu-id="ac9a2-131">Následující příklad používá `Not` operátor k provedení logické negace `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="ac9a2-132">Výsledkem je `Boolean` hodnota, která představuje obrácenou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="ac9a2-133">Předchozí příklad vytvoří výsledky a v `False` `True` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac9a2-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac9a2-134">Example</span></span>  
 <span data-ttu-id="ac9a2-135">Následující příklad používá `Not` operátor k provedení logické negace jednotlivých bitů číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="ac9a2-136">Bit ve vzorci výsledků je nastaven na zpětný výsledek odpovídajícího bitu ve vzoru operandu, včetně bitu znaménka.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="ac9a2-137">Předchozí příklad vytvoří výsledky – 11, – 9 a – 7 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ac9a2-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac9a2-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac9a2-138">See also</span></span>

- [<span data-ttu-id="ac9a2-139">Logické/bitové operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac9a2-139">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="ac9a2-140">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac9a2-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ac9a2-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ac9a2-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ac9a2-142">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac9a2-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
