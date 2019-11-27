---
title: / – operátor
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 537d8b0c703b59743f1a7c531448118058707645
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331057"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a0375-102">/ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0375-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="a0375-103">Vydělí dvě čísla a vrátí výsledek s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="a0375-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0375-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0375-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a0375-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a0375-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="a0375-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a0375-106">Required.</span></span> <span data-ttu-id="a0375-107">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a0375-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a0375-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a0375-108">Required.</span></span> <span data-ttu-id="a0375-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a0375-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="a0375-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="a0375-110">Supported Types</span></span>  
 <span data-ttu-id="a0375-111">Všechny číselné typy, včetně nepodepsaných typů a typů s plovoucí desetinnou čárkou a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a0375-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="a0375-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a0375-112">Result</span></span>  
 <span data-ttu-id="a0375-113">Výsledkem je úplný podíl `expression1` dělený `expression2`, včetně všech zbytků.</span><span class="sxs-lookup"><span data-stu-id="a0375-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="a0375-114">[Operátor \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselný podíl, který zbytek zruší.</span><span class="sxs-lookup"><span data-stu-id="a0375-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0375-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0375-115">Remarks</span></span>  
 <span data-ttu-id="a0375-116">Datový typ výsledku závisí na typech operandů.</span><span class="sxs-lookup"><span data-stu-id="a0375-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="a0375-117">Následující tabulka ukazuje, jak je určen datový typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="a0375-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="a0375-118">Datové typy operandů</span><span class="sxs-lookup"><span data-stu-id="a0375-118">Operand data types</span></span>|<span data-ttu-id="a0375-119">Výsledný datový typ</span><span class="sxs-lookup"><span data-stu-id="a0375-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="a0375-120">Oba výrazy jsou integrální datové typy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)).</span><span class="sxs-lookup"><span data-stu-id="a0375-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="a0375-121">Jeden výraz je [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) datový typ a druhý není typu [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="a0375-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="a0375-122">Jeden výraz je datový typ [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) a druhý není typu [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="a0375-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="a0375-123">Jeden z výrazů je datový typ [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="a0375-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="a0375-124">Před provedením dělení jsou všechny celočíselné číselné výrazy rozšířeny na `Double`.</span><span class="sxs-lookup"><span data-stu-id="a0375-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="a0375-125">Pokud přiřadíte výsledek celočíselnému datovému typu, Visual Basic se pokusí převést výsledek z `Double` na tento typ.</span><span class="sxs-lookup"><span data-stu-id="a0375-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="a0375-126">To může vyvolat výjimku, pokud výsledek se nevejde do tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a0375-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="a0375-127">Konkrétně naleznete na této stránce s touto stránkou "pokusy o dělení nulou".</span><span class="sxs-lookup"><span data-stu-id="a0375-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="a0375-128">Pokud se `expression1` nebo `expression2` vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude se jednat o nulu.</span><span class="sxs-lookup"><span data-stu-id="a0375-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="a0375-129">Došlo k pokusu o dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="a0375-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="a0375-130">Pokud `expression2` vyhodnotí jako nula, operátor `/` se chová jinak pro různé datové typy operandů.</span><span class="sxs-lookup"><span data-stu-id="a0375-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="a0375-131">V následující tabulce je uvedeno možné chování.</span><span class="sxs-lookup"><span data-stu-id="a0375-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="a0375-132">Datové typy operandů</span><span class="sxs-lookup"><span data-stu-id="a0375-132">Operand data types</span></span>|<span data-ttu-id="a0375-133">Chování, pokud je `expression2` nula</span><span class="sxs-lookup"><span data-stu-id="a0375-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="a0375-134">Plovoucí desetinná čárka (`Single` nebo `Double`)</span><span class="sxs-lookup"><span data-stu-id="a0375-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="a0375-135">Vrátí nekonečno (<xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>) nebo <xref:System.Double.NaN> (není číslo), pokud `expression1` je také nula.</span><span class="sxs-lookup"><span data-stu-id="a0375-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="a0375-136">Vyvolá <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="a0375-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="a0375-137">Celočíselný (podepsaný nebo nepodepsaný)</span><span class="sxs-lookup"><span data-stu-id="a0375-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="a0375-138">Pokus o převod zpět na celočíselný typ vyvolá <xref:System.OverflowException>, protože integrální typy nemůžou přijmout <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>nebo <xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="a0375-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a0375-139">Operátor `/` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="a0375-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a0375-140">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="a0375-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a0375-141">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a0375-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0375-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0375-142">Example</span></span>  
 <span data-ttu-id="a0375-143">V tomto příkladu se používá operátor `/` k provedení dělení s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="a0375-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="a0375-144">Výsledkem je podíl dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="a0375-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="a0375-145">Výrazy v předchozím příkladu vrací hodnoty 2,5 a 3,333333.</span><span class="sxs-lookup"><span data-stu-id="a0375-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="a0375-146">Všimněte si, že výsledek je vždy plovoucí desetinná čárka (`Double`), a to i v případě, že oba operandy jsou celočíselné konstanty.</span><span class="sxs-lookup"><span data-stu-id="a0375-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0375-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0375-147">See also</span></span>

- [<span data-ttu-id="a0375-148">/= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0375-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="a0375-149">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0375-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="a0375-150">Datové typy výsledků operátoru</span><span class="sxs-lookup"><span data-stu-id="a0375-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="a0375-151">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="a0375-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="a0375-152">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0375-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a0375-153">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="a0375-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a0375-154">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0375-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
