---
title: '&gt;&gt; Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 9bb8e82b3f5451417fe1867d08b7601ee1acb036
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605404"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="105a2-102">&gt;&gt; Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="105a2-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="105a2-103">Provede aritmetický správné posun bitový.</span><span class="sxs-lookup"><span data-stu-id="105a2-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="105a2-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="105a2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="105a2-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="105a2-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="105a2-106">Required.</span></span> <span data-ttu-id="105a2-107">Integrální číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="105a2-107">Integral numeric value.</span></span> <span data-ttu-id="105a2-108">Výsledek s posunem vzoru bit.</span><span class="sxs-lookup"><span data-stu-id="105a2-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="105a2-109">Typ dat je stejný jako u `pattern`.</span><span class="sxs-lookup"><span data-stu-id="105a2-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="105a2-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="105a2-110">Required.</span></span> <span data-ttu-id="105a2-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="105a2-111">Integral numeric expression.</span></span> <span data-ttu-id="105a2-112">Bitový posunutí.</span><span class="sxs-lookup"><span data-stu-id="105a2-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="105a2-113">Datový typ musí být typ integrální (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="105a2-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="105a2-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="105a2-114">Required.</span></span> <span data-ttu-id="105a2-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="105a2-115">Numeric expression.</span></span> <span data-ttu-id="105a2-116">Počet bitů se posunou vzoru bit.</span><span class="sxs-lookup"><span data-stu-id="105a2-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="105a2-117">Datový typ musí být `Integer` nebo rozšířit do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="105a2-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="105a2-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="105a2-118">Remarks</span></span>  
 <span data-ttu-id="105a2-119">Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="105a2-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="105a2-120">V aritmetické posunutí doprava bits zapuštěno nad rámec nejvíce vpravo bit pozice se zahodí a bit krajní levé (symbol) rozšířena do pozice bit vacated na levé straně.</span><span class="sxs-lookup"><span data-stu-id="105a2-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="105a2-121">To znamená, že pokud `pattern` má zápornou hodnotu vacated pozic jsou nastavené na jednu; jinak jsou nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="105a2-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="105a2-122">Všimněte si, že datové typy `Byte`, `UShort`, `UInteger`, a `ULong` jsou bez znaménka, proto neexistuje žádný přihlašovací bit rozšíření.</span><span class="sxs-lookup"><span data-stu-id="105a2-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="105a2-123">Pokud `pattern` je všechny nepodepsané typu, vacated pozic jsou vždy nastavená na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="105a2-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="105a2-124">Aby se zabránilo ve více bits, než mohou být uloženy výsledek s posunem, Visual Basic zakrývá hodnotu `amount` s maskou velikost odpovídající datový typ `pattern`.</span><span class="sxs-lookup"><span data-stu-id="105a2-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="105a2-125">Binární a z těchto hodnot se používá pro velikost shift.</span><span class="sxs-lookup"><span data-stu-id="105a2-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="105a2-126">Velikost masek jsou následující:</span><span class="sxs-lookup"><span data-stu-id="105a2-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="105a2-127">Datový typ `pattern`</span><span class="sxs-lookup"><span data-stu-id="105a2-127">Data type of `pattern`</span></span>|<span data-ttu-id="105a2-128">Velikost maska (decimální):</span><span class="sxs-lookup"><span data-stu-id="105a2-128">Size mask (decimal)</span></span>|<span data-ttu-id="105a2-129">Velikost maska (hexadecimální)</span><span class="sxs-lookup"><span data-stu-id="105a2-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="105a2-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="105a2-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="105a2-131">7</span><span class="sxs-lookup"><span data-stu-id="105a2-131">7</span></span>|<span data-ttu-id="105a2-132">&AMP; H00000007</span><span class="sxs-lookup"><span data-stu-id="105a2-132">&H00000007</span></span>|  
|<span data-ttu-id="105a2-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="105a2-133">`Short`, `UShort`</span></span>|<span data-ttu-id="105a2-134">15</span><span class="sxs-lookup"><span data-stu-id="105a2-134">15</span></span>|<span data-ttu-id="105a2-135">&AMP; H0000000F</span><span class="sxs-lookup"><span data-stu-id="105a2-135">&H0000000F</span></span>|  
|<span data-ttu-id="105a2-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="105a2-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="105a2-137">31</span><span class="sxs-lookup"><span data-stu-id="105a2-137">31</span></span>|<span data-ttu-id="105a2-138">&AMP; H0000001F</span><span class="sxs-lookup"><span data-stu-id="105a2-138">&H0000001F</span></span>|  
|<span data-ttu-id="105a2-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="105a2-139">`Long`, `ULong`</span></span>|<span data-ttu-id="105a2-140">63</span><span class="sxs-lookup"><span data-stu-id="105a2-140">63</span></span>|<span data-ttu-id="105a2-141">&AMP; H0000003F</span><span class="sxs-lookup"><span data-stu-id="105a2-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="105a2-142">Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`.</span><span class="sxs-lookup"><span data-stu-id="105a2-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="105a2-143">Pokud `amount` je záporná, je jako hodnotu bez znaménka a maskovat s maskou správnou velikost.</span><span class="sxs-lookup"><span data-stu-id="105a2-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="105a2-144">Aritmetické posuny nikdy generování výjimek přetečení.</span><span class="sxs-lookup"><span data-stu-id="105a2-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="105a2-145">Přetížení</span><span class="sxs-lookup"><span data-stu-id="105a2-145">Overloading</span></span>  
 <span data-ttu-id="105a2-146">`>>` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="105a2-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="105a2-147">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="105a2-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="105a2-148">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="105a2-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="105a2-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="105a2-149">Example</span></span>  
 <span data-ttu-id="105a2-150">Následující příklad používá `>>` operátor provést aritmetické posuny doprava na celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="105a2-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="105a2-151">Výsledek má vždy stejnou datový typ, který se zapuštěno výrazu.</span><span class="sxs-lookup"><span data-stu-id="105a2-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 <span data-ttu-id="105a2-152">Výsledky v předchozím příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="105a2-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="105a2-153">`result1` je 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="105a2-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="105a2-154">`result2` je 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="105a2-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="105a2-155">`result3` je 2 (0000 0000-0000 0010).</span><span class="sxs-lookup"><span data-stu-id="105a2-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="105a2-156">`result4` je 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="105a2-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="105a2-157">`result5` je 0 (posunuté 15 místech vpravo).</span><span class="sxs-lookup"><span data-stu-id="105a2-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="105a2-158">Velikost posunutí pro `result4` počítá se jako 18 a 15, který se rovná 2.</span><span class="sxs-lookup"><span data-stu-id="105a2-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="105a2-159">Následující příklad ukazuje aritmetické posuny na zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="105a2-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 <span data-ttu-id="105a2-160">Výsledky v předchozím příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="105a2-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="105a2-161">`negresult1` je -512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="105a2-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="105a2-162">`negresult2` je -1 (verze přihlašovací rozšířena).</span><span class="sxs-lookup"><span data-stu-id="105a2-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105a2-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="105a2-163">See Also</span></span>  
 [<span data-ttu-id="105a2-164">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="105a2-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="105a2-165">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="105a2-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="105a2-166">>>= – operátor</span><span class="sxs-lookup"><span data-stu-id="105a2-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [<span data-ttu-id="105a2-167">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="105a2-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="105a2-168">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="105a2-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="105a2-169">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="105a2-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
