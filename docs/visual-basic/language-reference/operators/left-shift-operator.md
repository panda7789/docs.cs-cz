---
title: "&lt;&lt;Operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56cfb227f7e5c68de802c1f2cfb842a770f65ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="6afba-102">&lt;&lt;Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6afba-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="6afba-103">Provede aritmetický levém posun bitový.</span><span class="sxs-lookup"><span data-stu-id="6afba-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6afba-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="6afba-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6afba-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6afba-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6afba-106">Required.</span></span> <span data-ttu-id="6afba-107">Integrální číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="6afba-107">Integral numeric value.</span></span> <span data-ttu-id="6afba-108">Výsledek s posunem vzoru bit.</span><span class="sxs-lookup"><span data-stu-id="6afba-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="6afba-109">Typ dat je stejný jako u `pattern`.</span><span class="sxs-lookup"><span data-stu-id="6afba-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="6afba-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6afba-110">Required.</span></span> <span data-ttu-id="6afba-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="6afba-111">Integral numeric expression.</span></span> <span data-ttu-id="6afba-112">Bitový posunutí.</span><span class="sxs-lookup"><span data-stu-id="6afba-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="6afba-113">Datový typ musí být typ integrální (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="6afba-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="6afba-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6afba-114">Required.</span></span> <span data-ttu-id="6afba-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="6afba-115">Numeric expression.</span></span> <span data-ttu-id="6afba-116">Počet bitů se posunou vzoru bit.</span><span class="sxs-lookup"><span data-stu-id="6afba-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="6afba-117">Datový typ musí být `Integer` nebo rozšířit do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6afba-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6afba-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6afba-118">Remarks</span></span>  
 <span data-ttu-id="6afba-119">Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="6afba-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="6afba-120">V aritmetické posunutí doleva jsou zahozeny bits zapuštěno mimo rozsah datového typu výsledek a pozice bit vacated na pravé straně nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="6afba-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="6afba-121">Pokud chcete zabránit posunutí ve více bits, než mohou být uloženy výsledek, Visual Basic zakrývá hodnotu `amount` s maskou velikost, která odpovídá datový typ `pattern`.</span><span class="sxs-lookup"><span data-stu-id="6afba-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="6afba-122">Binární a z těchto hodnot se používá pro velikost shift.</span><span class="sxs-lookup"><span data-stu-id="6afba-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="6afba-123">Velikost masek jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6afba-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="6afba-124">Datový typ`pattern`</span><span class="sxs-lookup"><span data-stu-id="6afba-124">Data type of `pattern`</span></span>|<span data-ttu-id="6afba-125">Velikost maska (decimální):</span><span class="sxs-lookup"><span data-stu-id="6afba-125">Size mask (decimal)</span></span>|<span data-ttu-id="6afba-126">Velikost maska (hexadecimální)</span><span class="sxs-lookup"><span data-stu-id="6afba-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="6afba-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="6afba-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="6afba-128">7</span><span class="sxs-lookup"><span data-stu-id="6afba-128">7</span></span>|<span data-ttu-id="6afba-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="6afba-129">&H00000007</span></span>|  
|<span data-ttu-id="6afba-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="6afba-130">`Short`, `UShort`</span></span>|<span data-ttu-id="6afba-131">15</span><span class="sxs-lookup"><span data-stu-id="6afba-131">15</span></span>|<span data-ttu-id="6afba-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="6afba-132">&H0000000F</span></span>|  
|<span data-ttu-id="6afba-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="6afba-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="6afba-134">31</span><span class="sxs-lookup"><span data-stu-id="6afba-134">31</span></span>|<span data-ttu-id="6afba-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="6afba-135">&H0000001F</span></span>|  
|<span data-ttu-id="6afba-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="6afba-136">`Long`, `ULong`</span></span>|<span data-ttu-id="6afba-137">63</span><span class="sxs-lookup"><span data-stu-id="6afba-137">63</span></span>|<span data-ttu-id="6afba-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="6afba-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="6afba-139">Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`.</span><span class="sxs-lookup"><span data-stu-id="6afba-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="6afba-140">Pokud `amount` je záporná, je jako hodnotu bez znaménka a maskovat s maskou správnou velikost.</span><span class="sxs-lookup"><span data-stu-id="6afba-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="6afba-141">Aritmetické posuny nikdy generování výjimek přetečení.</span><span class="sxs-lookup"><span data-stu-id="6afba-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6afba-142">`<<` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="6afba-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6afba-143">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="6afba-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="6afba-144">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6afba-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6afba-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="6afba-145">Example</span></span>  
 <span data-ttu-id="6afba-146">Následující příklad používá `<<` operátor provést aritmetické zbývajících posuny na celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6afba-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="6afba-147">Výsledek má vždy stejnou datový typ, který se zapuštěno výrazu.</span><span class="sxs-lookup"><span data-stu-id="6afba-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="6afba-148">Výsledky v předchozím příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6afba-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="6afba-149">`result1`je 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="6afba-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="6afba-150">`result2`je 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="6afba-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="6afba-151">`result3`je-32 768 (1000 0000-0000 0000).</span><span class="sxs-lookup"><span data-stu-id="6afba-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="6afba-152">`result4`je 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="6afba-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="6afba-153">`result5`je 0 (posunuté 15 místa vlevo).</span><span class="sxs-lookup"><span data-stu-id="6afba-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="6afba-154">Velikost posunutí pro `result4` počítá se jako 17 a 15, který se rovná 1.</span><span class="sxs-lookup"><span data-stu-id="6afba-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afba-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="6afba-155">See Also</span></span>  
 [<span data-ttu-id="6afba-156">Operátory bitového posunutí</span><span class="sxs-lookup"><span data-stu-id="6afba-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="6afba-157">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="6afba-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="6afba-158"><< = – operátor</span><span class="sxs-lookup"><span data-stu-id="6afba-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [<span data-ttu-id="6afba-159">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6afba-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="6afba-160">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="6afba-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="6afba-161">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6afba-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
