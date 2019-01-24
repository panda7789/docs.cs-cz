---
title: '&lt;&lt; – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d39a134390591e3c72887a38e8aacb4631c71d87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539035"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="8b89a-102">&lt;&lt; – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b89a-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="8b89a-103">Provede aritmetický operátor posunu vlevo bitový vzor.</span><span class="sxs-lookup"><span data-stu-id="8b89a-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b89a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b89a-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="8b89a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8b89a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8b89a-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8b89a-106">Required.</span></span> <span data-ttu-id="8b89a-107">Integrální číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8b89a-107">Integral numeric value.</span></span> <span data-ttu-id="8b89a-108">Výsledek posunu bitový vzor.</span><span class="sxs-lookup"><span data-stu-id="8b89a-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="8b89a-109">Datový typ je stejné jako u `pattern`.</span><span class="sxs-lookup"><span data-stu-id="8b89a-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="8b89a-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8b89a-110">Required.</span></span> <span data-ttu-id="8b89a-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="8b89a-111">Integral numeric expression.</span></span> <span data-ttu-id="8b89a-112">Bitový vzor posunutí.</span><span class="sxs-lookup"><span data-stu-id="8b89a-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="8b89a-113">Datový typ musí být celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="8b89a-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="8b89a-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8b89a-114">Required.</span></span> <span data-ttu-id="8b89a-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="8b89a-115">Numeric expression.</span></span> <span data-ttu-id="8b89a-116">Počet bitů, chcete-li posunout bitový vzor.</span><span class="sxs-lookup"><span data-stu-id="8b89a-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="8b89a-117">Datový typ musí být `Integer` nebo rozšířit na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8b89a-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b89a-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b89a-118">Remarks</span></span>  
 <span data-ttu-id="8b89a-119">Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek.</span><span class="sxs-lookup"><span data-stu-id="8b89a-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="8b89a-120">V aritmetických posunutí doleva bity posunuta mimo rozsah datového typu výsledku ignorovány a bitové pozice uvolněné na pravé straně jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="8b89a-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="8b89a-121">Aby shift ve více bitů než výsledek může obsahovat jazyka Visual Basic zakrývá hodnotu `amount` s maskou velikost, která odpovídá datovému typu `pattern`.</span><span class="sxs-lookup"><span data-stu-id="8b89a-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="8b89a-122">Binární a tyto hodnoty se používá pro hodnota shift.</span><span class="sxs-lookup"><span data-stu-id="8b89a-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="8b89a-123">Velikost masky jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8b89a-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="8b89a-124">Datový typ `pattern`</span><span class="sxs-lookup"><span data-stu-id="8b89a-124">Data type of `pattern`</span></span>|<span data-ttu-id="8b89a-125">Maska velikost (decimální)</span><span class="sxs-lookup"><span data-stu-id="8b89a-125">Size mask (decimal)</span></span>|<span data-ttu-id="8b89a-126">Maska velikost (v šestnáctkové hodnotě)</span><span class="sxs-lookup"><span data-stu-id="8b89a-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="8b89a-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="8b89a-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="8b89a-128">7</span><span class="sxs-lookup"><span data-stu-id="8b89a-128">7</span></span>|<span data-ttu-id="8b89a-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="8b89a-129">&H00000007</span></span>|  
|<span data-ttu-id="8b89a-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="8b89a-130">`Short`, `UShort`</span></span>|<span data-ttu-id="8b89a-131">15</span><span class="sxs-lookup"><span data-stu-id="8b89a-131">15</span></span>|<span data-ttu-id="8b89a-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="8b89a-132">&H0000000F</span></span>|  
|<span data-ttu-id="8b89a-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="8b89a-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="8b89a-134">31</span><span class="sxs-lookup"><span data-stu-id="8b89a-134">31</span></span>|<span data-ttu-id="8b89a-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="8b89a-135">&H0000001F</span></span>|  
|<span data-ttu-id="8b89a-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="8b89a-136">`Long`, `ULong`</span></span>|<span data-ttu-id="8b89a-137">63</span><span class="sxs-lookup"><span data-stu-id="8b89a-137">63</span></span>|<span data-ttu-id="8b89a-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="8b89a-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="8b89a-139">Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`.</span><span class="sxs-lookup"><span data-stu-id="8b89a-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="8b89a-140">Pokud `amount` je záporný, je provedena jako hodnoty bez znaménka a maskována pomocí masky odpovídající velikost.</span><span class="sxs-lookup"><span data-stu-id="8b89a-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="8b89a-141">Aritmetické staffhubu nikdy generovat výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="8b89a-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b89a-142">`<<` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="8b89a-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8b89a-143">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="8b89a-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="8b89a-144">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8b89a-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b89a-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b89a-145">Example</span></span>  
 <span data-ttu-id="8b89a-146">V následujícím příkladu `<<` operátor aritmetické operace na integrální hodnoty posune doleva.</span><span class="sxs-lookup"><span data-stu-id="8b89a-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="8b89a-147">Výsledek je vždy stejný datový typ jako, který se posune výrazu.</span><span class="sxs-lookup"><span data-stu-id="8b89a-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="8b89a-148">Výsledky v předchozím příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8b89a-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="8b89a-149">`result1` is 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="8b89a-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="8b89a-150">`result2` is 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="8b89a-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="8b89a-151">`result3` is -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="8b89a-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="8b89a-152">`result4` is 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="8b89a-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="8b89a-153">`result5` je 0 (posunuté 15 míst na levé straně).</span><span class="sxs-lookup"><span data-stu-id="8b89a-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="8b89a-154">Hodnota shift pro `result4` se vypočte takto: 17 a 15, které se rovná 1.</span><span class="sxs-lookup"><span data-stu-id="8b89a-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b89a-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b89a-155">See also</span></span>
- [<span data-ttu-id="8b89a-156">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="8b89a-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="8b89a-157">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="8b89a-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8b89a-158"><<= – operátor</span><span class="sxs-lookup"><span data-stu-id="8b89a-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="8b89a-159">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b89a-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8b89a-160">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="8b89a-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8b89a-161">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b89a-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
