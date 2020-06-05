---
title: << – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 1128b32a739e7dbf3893dcd19b37247cd4643c85
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370632"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0fe27-102">\<\<– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fe27-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="0fe27-103">Provede aritmetický levý posun na bitový vzorek.</span><span class="sxs-lookup"><span data-stu-id="0fe27-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fe27-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="0fe27-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0fe27-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0fe27-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0fe27-106">Required.</span></span> <span data-ttu-id="0fe27-107">Integrální číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0fe27-107">Integral numeric value.</span></span> <span data-ttu-id="0fe27-108">Výsledek posunu bitového vzoru.</span><span class="sxs-lookup"><span data-stu-id="0fe27-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="0fe27-109">Datový typ je stejný jako u `pattern` .</span><span class="sxs-lookup"><span data-stu-id="0fe27-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="0fe27-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0fe27-110">Required.</span></span> <span data-ttu-id="0fe27-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="0fe27-111">Integral numeric expression.</span></span> <span data-ttu-id="0fe27-112">Bitový vzorek, který se má posunout.</span><span class="sxs-lookup"><span data-stu-id="0fe27-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="0fe27-113">Datový typ musí být integrální typ ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="0fe27-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="0fe27-114">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0fe27-114">Required.</span></span> <span data-ttu-id="0fe27-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="0fe27-115">Numeric expression.</span></span> <span data-ttu-id="0fe27-116">Počet bitů pro posunutí bitového vzoru.</span><span class="sxs-lookup"><span data-stu-id="0fe27-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="0fe27-117">Datový typ musí být `Integer` nebo rozšířit na `Integer` .</span><span class="sxs-lookup"><span data-stu-id="0fe27-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fe27-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fe27-118">Remarks</span></span>  
 <span data-ttu-id="0fe27-119">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="0fe27-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="0fe27-120">V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="0fe27-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="0fe27-121">Aby se zabránilo posunu více bitů, než je výsledek, Visual Basic maskuje hodnotu `amount` s maskou velikosti, která odpovídá datovému typu `pattern` .</span><span class="sxs-lookup"><span data-stu-id="0fe27-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="0fe27-122">Binární soubor a tyto hodnoty se použijí pro velikost Shift.</span><span class="sxs-lookup"><span data-stu-id="0fe27-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="0fe27-123">Masky velikosti jsou následující:</span><span class="sxs-lookup"><span data-stu-id="0fe27-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="0fe27-124">Datový typ`pattern`</span><span class="sxs-lookup"><span data-stu-id="0fe27-124">Data type of `pattern`</span></span>|<span data-ttu-id="0fe27-125">Velikost – maska (desítková)</span><span class="sxs-lookup"><span data-stu-id="0fe27-125">Size mask (decimal)</span></span>|<span data-ttu-id="0fe27-126">Velikost – maska (šestnáctkově)</span><span class="sxs-lookup"><span data-stu-id="0fe27-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="0fe27-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="0fe27-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="0fe27-128">7</span><span class="sxs-lookup"><span data-stu-id="0fe27-128">7</span></span>|<span data-ttu-id="0fe27-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="0fe27-129">&H00000007</span></span>|  
|<span data-ttu-id="0fe27-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="0fe27-130">`Short`, `UShort`</span></span>|<span data-ttu-id="0fe27-131">15</span><span class="sxs-lookup"><span data-stu-id="0fe27-131">15</span></span>|<span data-ttu-id="0fe27-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="0fe27-132">&H0000000F</span></span>|  
|<span data-ttu-id="0fe27-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="0fe27-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="0fe27-134">31</span><span class="sxs-lookup"><span data-stu-id="0fe27-134">31</span></span>|<span data-ttu-id="0fe27-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="0fe27-135">&H0000001F</span></span>|  
|<span data-ttu-id="0fe27-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="0fe27-136">`Long`, `ULong`</span></span>|<span data-ttu-id="0fe27-137">63</span><span class="sxs-lookup"><span data-stu-id="0fe27-137">63</span></span>|<span data-ttu-id="0fe27-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="0fe27-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="0fe27-139">Pokud `amount` je nula, hodnota `result` je shodná s hodnotou `pattern` .</span><span class="sxs-lookup"><span data-stu-id="0fe27-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="0fe27-140">Pokud `amount` je záporná, je pořízena jako hodnota bez znaménka a maskována odpovídající maskou velikosti.</span><span class="sxs-lookup"><span data-stu-id="0fe27-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="0fe27-141">Aritmetické posuny nikdy negenerují výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="0fe27-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fe27-142">`<<`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0fe27-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0fe27-143">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="0fe27-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="0fe27-144">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0fe27-144">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fe27-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fe27-145">Example</span></span>  
 <span data-ttu-id="0fe27-146">Následující příklad používá `<<` operátor k provádění aritmetických operací doleva u integrálních hodnot.</span><span class="sxs-lookup"><span data-stu-id="0fe27-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="0fe27-147">Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.</span><span class="sxs-lookup"><span data-stu-id="0fe27-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="0fe27-148">Výsledky předchozího příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="0fe27-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="0fe27-149">`result1`je 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="0fe27-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="0fe27-150">`result2`je 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="0fe27-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="0fe27-151">`result3`je-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="0fe27-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="0fe27-152">`result4`je 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="0fe27-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="0fe27-153">`result5`je 0 (posun 15 míst doleva).</span><span class="sxs-lookup"><span data-stu-id="0fe27-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="0fe27-154">Hodnota posunu pro `result4` se počítá jako 17 a 15, což se rovná 1.</span><span class="sxs-lookup"><span data-stu-id="0fe27-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe27-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fe27-155">See also</span></span>

- [<span data-ttu-id="0fe27-156">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="0fe27-156">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="0fe27-157">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="0fe27-157">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="0fe27-158"><<= – operátor</span><span class="sxs-lookup"><span data-stu-id="0fe27-158"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="0fe27-159">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fe27-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0fe27-160">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0fe27-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0fe27-161">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fe27-161">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
