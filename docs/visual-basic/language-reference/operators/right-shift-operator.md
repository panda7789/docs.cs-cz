---
title: '>> Operátor'
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
ms.openlocfilehash: 10b07da22b8b43d6a966fa7c334ac6a0ef4b430d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406363"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="91961-102">Operátor >> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91961-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="91961-103">Provede aritmetický pravý posun na bitový vzorek.</span><span class="sxs-lookup"><span data-stu-id="91961-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91961-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91961-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="91961-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="91961-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="91961-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="91961-106">Required.</span></span> <span data-ttu-id="91961-107">Integrální číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="91961-107">Integral numeric value.</span></span> <span data-ttu-id="91961-108">Výsledek posunu bitového vzoru.</span><span class="sxs-lookup"><span data-stu-id="91961-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="91961-109">Datový typ je stejný jako u `pattern` .</span><span class="sxs-lookup"><span data-stu-id="91961-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="91961-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="91961-110">Required.</span></span> <span data-ttu-id="91961-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="91961-111">Integral numeric expression.</span></span> <span data-ttu-id="91961-112">Bitový vzorek, který se má posunout.</span><span class="sxs-lookup"><span data-stu-id="91961-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="91961-113">Datový typ musí být integrální typ ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="91961-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="91961-114">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="91961-114">Required.</span></span> <span data-ttu-id="91961-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="91961-115">Numeric expression.</span></span> <span data-ttu-id="91961-116">Počet bitů pro posunutí bitového vzoru.</span><span class="sxs-lookup"><span data-stu-id="91961-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="91961-117">Datový typ musí být `Integer` nebo rozšířit na `Integer` .</span><span class="sxs-lookup"><span data-stu-id="91961-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91961-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91961-118">Remarks</span></span>  
 <span data-ttu-id="91961-119">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="91961-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="91961-120">V aritmetickém pravém posunu se bity, které přesahují napravo od pozice vpravo, zahodí a bit úplně vlevo (znaménko) se rozšíří do bitových pozic uvolněné vlevo.</span><span class="sxs-lookup"><span data-stu-id="91961-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="91961-121">To znamená, že pokud `pattern` má zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu; v opačném případě jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="91961-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="91961-122">Všimněte si, že datové typy `Byte` , `UShort` , `UInteger` a `ULong` jsou bez znaménka, takže neexistuje bit znaménka pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="91961-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="91961-123">Pokud `pattern` je jakýkoli typ bez znaménka, pozice uvolněné jsou vždy nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="91961-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="91961-124">Aby nedocházelo k posunu více bitů, než může výsledek uchovávat, Visual Basic maskuje hodnotu `amount` s maskou velikosti odpovídající datovému typu `pattern` .</span><span class="sxs-lookup"><span data-stu-id="91961-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="91961-125">Binární soubor a tyto hodnoty se použijí pro velikost Shift.</span><span class="sxs-lookup"><span data-stu-id="91961-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="91961-126">Masky velikosti jsou následující:</span><span class="sxs-lookup"><span data-stu-id="91961-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="91961-127">Datový typ`pattern`</span><span class="sxs-lookup"><span data-stu-id="91961-127">Data type of `pattern`</span></span>|<span data-ttu-id="91961-128">Velikost – maska (desítková)</span><span class="sxs-lookup"><span data-stu-id="91961-128">Size mask (decimal)</span></span>|<span data-ttu-id="91961-129">Velikost – maska (šestnáctkově)</span><span class="sxs-lookup"><span data-stu-id="91961-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="91961-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="91961-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="91961-131">7</span><span class="sxs-lookup"><span data-stu-id="91961-131">7</span></span>|<span data-ttu-id="91961-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="91961-132">&H00000007</span></span>|  
|<span data-ttu-id="91961-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="91961-133">`Short`, `UShort`</span></span>|<span data-ttu-id="91961-134">15</span><span class="sxs-lookup"><span data-stu-id="91961-134">15</span></span>|<span data-ttu-id="91961-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="91961-135">&H0000000F</span></span>|  
|<span data-ttu-id="91961-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="91961-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="91961-137">31</span><span class="sxs-lookup"><span data-stu-id="91961-137">31</span></span>|<span data-ttu-id="91961-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="91961-138">&H0000001F</span></span>|  
|<span data-ttu-id="91961-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="91961-139">`Long`, `ULong`</span></span>|<span data-ttu-id="91961-140">63</span><span class="sxs-lookup"><span data-stu-id="91961-140">63</span></span>|<span data-ttu-id="91961-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="91961-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="91961-142">Pokud `amount` je nula, hodnota `result` je shodná s hodnotou `pattern` .</span><span class="sxs-lookup"><span data-stu-id="91961-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="91961-143">Pokud `amount` je záporná, je pořízena jako hodnota bez znaménka a maskována odpovídající maskou velikosti.</span><span class="sxs-lookup"><span data-stu-id="91961-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="91961-144">Aritmetické posuny nikdy negenerují výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="91961-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="91961-145">Přetížení</span><span class="sxs-lookup"><span data-stu-id="91961-145">Overloading</span></span>  
 <span data-ttu-id="91961-146">`>>`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="91961-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="91961-147">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="91961-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="91961-148">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="91961-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91961-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="91961-149">Example</span></span>  
 <span data-ttu-id="91961-150">Následující příklad používá `>>` operátor k provádění aritmetických pravých posunů u integrálních hodnot.</span><span class="sxs-lookup"><span data-stu-id="91961-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="91961-151">Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.</span><span class="sxs-lookup"><span data-stu-id="91961-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="91961-152">Výsledky předchozího příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="91961-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="91961-153">`result1`je 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="91961-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="91961-154">`result2`je 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="91961-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="91961-155">`result3`je 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="91961-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="91961-156">`result4`je 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="91961-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="91961-157">`result5`je 0 (posun 15 míst doprava).</span><span class="sxs-lookup"><span data-stu-id="91961-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="91961-158">Hodnota posunu pro `result4` se počítá jako 18 a 15, což se rovná 2.</span><span class="sxs-lookup"><span data-stu-id="91961-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="91961-159">Následující příklad ukazuje aritmetické posuny na zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91961-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="91961-160">Výsledky předchozího příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="91961-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="91961-161">`negresult1`je-512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="91961-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="91961-162">`negresult2`je-1 (bit znaménka je šířen).</span><span class="sxs-lookup"><span data-stu-id="91961-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91961-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="91961-163">See also</span></span>

- [<span data-ttu-id="91961-164">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="91961-164">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="91961-165">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="91961-165">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="91961-166">>>= – operátor</span><span class="sxs-lookup"><span data-stu-id="91961-166">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="91961-167">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91961-167">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="91961-168">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="91961-168">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="91961-169">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91961-169">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
