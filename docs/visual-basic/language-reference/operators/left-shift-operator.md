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
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350985"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ab5b5-102">Operátor \<\< (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab5b5-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="ab5b5-103">Provede aritmetický levý posun na bitový vzorek.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab5b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab5b5-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="ab5b5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ab5b5-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="ab5b5-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-106">Required.</span></span> <span data-ttu-id="ab5b5-107">Integrální číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-107">Integral numeric value.</span></span> <span data-ttu-id="ab5b5-108">Výsledek posunu bitového vzoru.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="ab5b5-109">Datový typ je stejný jako u `pattern`.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="ab5b5-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-110">Required.</span></span> <span data-ttu-id="ab5b5-111">Integrální číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-111">Integral numeric expression.</span></span> <span data-ttu-id="ab5b5-112">Bitový vzorek, který se má posunout.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="ab5b5-113">Datový typ musí být integrální typ (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="ab5b5-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-114">Required.</span></span> <span data-ttu-id="ab5b5-115">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-115">Numeric expression.</span></span> <span data-ttu-id="ab5b5-116">Počet bitů pro posunutí bitového vzoru.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="ab5b5-117">Datový typ musí být `Integer` nebo se rozšířit na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab5b5-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab5b5-118">Remarks</span></span>  
 <span data-ttu-id="ab5b5-119">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="ab5b5-120">V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="ab5b5-121">Aby se zabránilo posunu více bitů, než je výsledek, Visual Basic maskuje hodnotu `amount` s maskou velikosti, která odpovídá datovému typu `pattern`.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="ab5b5-122">Binární soubor a tyto hodnoty se použijí pro velikost Shift.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="ab5b5-123">Masky velikosti jsou následující:</span><span class="sxs-lookup"><span data-stu-id="ab5b5-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="ab5b5-124">Datový typ `pattern`</span><span class="sxs-lookup"><span data-stu-id="ab5b5-124">Data type of `pattern`</span></span>|<span data-ttu-id="ab5b5-125">Velikost – maska (desítková)</span><span class="sxs-lookup"><span data-stu-id="ab5b5-125">Size mask (decimal)</span></span>|<span data-ttu-id="ab5b5-126">Velikost – maska (šestnáctkově)</span><span class="sxs-lookup"><span data-stu-id="ab5b5-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="ab5b5-127">`SByte``Byte`</span><span class="sxs-lookup"><span data-stu-id="ab5b5-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="ab5b5-128">7</span><span class="sxs-lookup"><span data-stu-id="ab5b5-128">7</span></span>|<span data-ttu-id="ab5b5-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="ab5b5-129">&H00000007</span></span>|  
|<span data-ttu-id="ab5b5-130">`Short``UShort`</span><span class="sxs-lookup"><span data-stu-id="ab5b5-130">`Short`, `UShort`</span></span>|<span data-ttu-id="ab5b5-131">15</span><span class="sxs-lookup"><span data-stu-id="ab5b5-131">15</span></span>|<span data-ttu-id="ab5b5-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="ab5b5-132">&H0000000F</span></span>|  
|<span data-ttu-id="ab5b5-133">`Integer``UInteger`</span><span class="sxs-lookup"><span data-stu-id="ab5b5-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="ab5b5-134">31</span><span class="sxs-lookup"><span data-stu-id="ab5b5-134">31</span></span>|<span data-ttu-id="ab5b5-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="ab5b5-135">&H0000001F</span></span>|  
|<span data-ttu-id="ab5b5-136">`Long``ULong`</span><span class="sxs-lookup"><span data-stu-id="ab5b5-136">`Long`, `ULong`</span></span>|<span data-ttu-id="ab5b5-137">63</span><span class="sxs-lookup"><span data-stu-id="ab5b5-137">63</span></span>|<span data-ttu-id="ab5b5-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="ab5b5-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="ab5b5-139">Pokud je `amount` nula, hodnota `result` je shodná s hodnotou `pattern`.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="ab5b5-140">Pokud je `amount` záporné, je převedena jako hodnota bez znaménka a s maskou odpovídající velikosti.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="ab5b5-141">Aritmetické posuny nikdy negenerují výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab5b5-142">Operátor `<<` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ab5b5-143">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="ab5b5-144">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab5b5-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab5b5-145">Example</span></span>  
 <span data-ttu-id="ab5b5-146">Následující příklad používá operátor `<<` k provádění aritmetických posunů v celočíselných hodnotách.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="ab5b5-147">Výsledek má vždycky stejný datový typ jako výraz, který se posouvá.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="ab5b5-148">Výsledky předchozího příkladu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="ab5b5-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="ab5b5-149">`result1` je 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="ab5b5-150">`result2` je 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="ab5b5-151">`result3` je-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="ab5b5-152">`result4` je 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="ab5b5-153">`result5` je 0 (přesune se na 15 míst vlevo).</span><span class="sxs-lookup"><span data-stu-id="ab5b5-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="ab5b5-154">Velikost posunutí pro `result4` se počítá jako 17 a 15, což se rovná 1.</span><span class="sxs-lookup"><span data-stu-id="ab5b5-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5b5-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab5b5-155">See also</span></span>

- [<span data-ttu-id="ab5b5-156">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="ab5b5-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="ab5b5-157">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="ab5b5-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="ab5b5-158"><<= – operátor</span><span class="sxs-lookup"><span data-stu-id="ab5b5-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="ab5b5-159">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab5b5-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ab5b5-160">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ab5b5-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ab5b5-161">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab5b5-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
