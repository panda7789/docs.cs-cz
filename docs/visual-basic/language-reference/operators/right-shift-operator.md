---
title: '>> – Operátor (Visual Basic)'
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
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816964"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f6ee9-102">>> – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6ee9-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="f6ee9-103">Provede aritmetický posunutí doprava bitový vzor.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ee9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6ee9-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="f6ee9-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f6ee9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f6ee9-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-106">Required.</span></span> <span data-ttu-id="f6ee9-107">Integrální číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-107">Integral numeric value.</span></span> <span data-ttu-id="f6ee9-108">Výsledek posunu bitový vzor.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="f6ee9-109">Datový typ je stejné jako u `pattern`.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="f6ee9-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-110">Required.</span></span> <span data-ttu-id="f6ee9-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-111">Integral numeric expression.</span></span> <span data-ttu-id="f6ee9-112">Bitový vzor posunutí.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="f6ee9-113">Datový typ musí být celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="f6ee9-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-114">Required.</span></span> <span data-ttu-id="f6ee9-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-115">Numeric expression.</span></span> <span data-ttu-id="f6ee9-116">Počet bitů, chcete-li posunout bitový vzor.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="f6ee9-117">Datový typ musí být `Integer` nebo rozšířit na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6ee9-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6ee9-118">Remarks</span></span>  
 <span data-ttu-id="f6ee9-119">Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="f6ee9-120">V aritmetické posunutí doprava bity posunuta nad rámec úplně vpravo bitová pozice se zahodí a bit nejvíce vlevo (sign) je postoupena do bitové pozice uvolněné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="f6ee9-121">To znamená, že pokud `pattern` má zápornou hodnotu uvolněných pozic jsou nastavené na jednu; v opačném případě jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="f6ee9-122">Všimněte si, že datové typy, které `Byte`, `UShort`, `UInteger`, a `ULong` jsou bez znaménka, takže neexistuje žádný bit znaménka rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="f6ee9-123">Pokud `pattern` je některý typ bez znaménka, uvolněných pozic jsou vždy nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="f6ee9-124">Aby posunutí ve více bitů než výsledek může obsahovat jazyka Visual Basic zakrývá hodnotu `amount` s maskou velikost odpovídající datový typ `pattern`.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="f6ee9-125">Binární a tyto hodnoty se používá pro hodnota shift.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="f6ee9-126">Velikost masky jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f6ee9-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="f6ee9-127">Datový typ `pattern`</span><span class="sxs-lookup"><span data-stu-id="f6ee9-127">Data type of `pattern`</span></span>|<span data-ttu-id="f6ee9-128">Maska velikost (decimální)</span><span class="sxs-lookup"><span data-stu-id="f6ee9-128">Size mask (decimal)</span></span>|<span data-ttu-id="f6ee9-129">Maska velikost (v šestnáctkové hodnotě)</span><span class="sxs-lookup"><span data-stu-id="f6ee9-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="f6ee9-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="f6ee9-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="f6ee9-131">7</span><span class="sxs-lookup"><span data-stu-id="f6ee9-131">7</span></span>|<span data-ttu-id="f6ee9-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="f6ee9-132">&H00000007</span></span>|  
|<span data-ttu-id="f6ee9-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="f6ee9-133">`Short`, `UShort`</span></span>|<span data-ttu-id="f6ee9-134">15</span><span class="sxs-lookup"><span data-stu-id="f6ee9-134">15</span></span>|<span data-ttu-id="f6ee9-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="f6ee9-135">&H0000000F</span></span>|  
|<span data-ttu-id="f6ee9-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="f6ee9-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="f6ee9-137">31</span><span class="sxs-lookup"><span data-stu-id="f6ee9-137">31</span></span>|<span data-ttu-id="f6ee9-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="f6ee9-138">&H0000001F</span></span>|  
|<span data-ttu-id="f6ee9-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="f6ee9-139">`Long`, `ULong`</span></span>|<span data-ttu-id="f6ee9-140">63</span><span class="sxs-lookup"><span data-stu-id="f6ee9-140">63</span></span>|<span data-ttu-id="f6ee9-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="f6ee9-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="f6ee9-142">Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="f6ee9-143">Pokud `amount` je záporný, je provedena jako hodnoty bez znaménka a maskována pomocí masky odpovídající velikost.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="f6ee9-144">Aritmetické staffhubu nikdy generovat výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f6ee9-145">Přetížení</span><span class="sxs-lookup"><span data-stu-id="f6ee9-145">Overloading</span></span>  
 <span data-ttu-id="f6ee9-146">`>>` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f6ee9-147">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f6ee9-148">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6ee9-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6ee9-149">Example</span></span>  
 <span data-ttu-id="f6ee9-150">V následujícím příkladu `>>` operátor aritmetické posuny doprava na integrální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="f6ee9-151">Výsledek je vždy stejný datový typ jako, který se posune výrazu.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="f6ee9-152">Výsledky v předchozím příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f6ee9-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="f6ee9-153">`result1` is 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="f6ee9-154">`result2` je 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="f6ee9-155">`result3` is 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="f6ee9-156">`result4` is 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="f6ee9-157">`result5` je 0 (posunuté 15 míst napravo).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="f6ee9-158">Hodnota shift pro `result4` se vypočte takto: 18 a 15, které se rovná 2.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="f6ee9-159">Následující příklad ukazuje aritmetické staffhubu na zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6ee9-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="f6ee9-160">Výsledky v předchozím příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f6ee9-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="f6ee9-161">`negresult1` is -512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="f6ee9-162">`negresult2` je -1 (rozšířeno na bit znaménka).</span><span class="sxs-lookup"><span data-stu-id="f6ee9-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ee9-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6ee9-163">See also</span></span>

- [<span data-ttu-id="f6ee9-164">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="f6ee9-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="f6ee9-165">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="f6ee9-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="f6ee9-166">>>= – operátor</span><span class="sxs-lookup"><span data-stu-id="f6ee9-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="f6ee9-167">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6ee9-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f6ee9-168">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="f6ee9-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f6ee9-169">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6ee9-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
