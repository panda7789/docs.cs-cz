---
title: "/ – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f221e863725b9aeb0b3fa3219b3a881541e2be0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e421e-102">/ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e421e-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="e421e-103">Provede podíl dvou čísel a vrátí výsledek s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="e421e-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e421e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e421e-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e421e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e421e-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="e421e-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e421e-106">Required.</span></span> <span data-ttu-id="e421e-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="e421e-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="e421e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e421e-108">Required.</span></span> <span data-ttu-id="e421e-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="e421e-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="e421e-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="e421e-110">Supported Types</span></span>  
 <span data-ttu-id="e421e-111">Všechny číselné typy, včetně typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e421e-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="e421e-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="e421e-112">Result</span></span>  
 <span data-ttu-id="e421e-113">Výsledkem je úplná podíl `expression1` dělený `expression2`, včetně všech zbytek.</span><span class="sxs-lookup"><span data-stu-id="e421e-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="e421e-114">[\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselný koeficient, který zahodí zbytek.</span><span class="sxs-lookup"><span data-stu-id="e421e-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e421e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e421e-115">Remarks</span></span>  
 <span data-ttu-id="e421e-116">Datový typ výsledku závisí na typech operandy.</span><span class="sxs-lookup"><span data-stu-id="e421e-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="e421e-117">Následující tabulka uvádí, jakým způsobem je určován datový typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="e421e-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="e421e-118">Operand datové typy</span><span class="sxs-lookup"><span data-stu-id="e421e-118">Operand data types</span></span>|<span data-ttu-id="e421e-119">Výsledek datový typ</span><span class="sxs-lookup"><span data-stu-id="e421e-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="e421e-120">Integrální datové typy jsou oba výrazy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krátké](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [dlouho](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="e421e-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="e421e-121">Je jeden výraz [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) datový typ a druhá není [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="e421e-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="e421e-122">Je jeden výraz [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) datový typ a druhá není [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="e421e-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="e421e-123">Buď výraz [dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) datový typ</span><span class="sxs-lookup"><span data-stu-id="e421e-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="e421e-124">Před dělení, jsou všechny výrazy integrálních číselné rozšířit do `Double`.</span><span class="sxs-lookup"><span data-stu-id="e421e-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="e421e-125">Chcete-li přiřadit výsledek celočíselný datový typ, se pokusí převést výsledek z jazyka Visual Basic `Double` do daného typu.</span><span class="sxs-lookup"><span data-stu-id="e421e-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="e421e-126">To může vyvolat výjimku, pokud výsledek nevejde do typu.</span><span class="sxs-lookup"><span data-stu-id="e421e-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="e421e-127">Konkrétně najdete v části "Se pokusil dělení podle nula" na této stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="e421e-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="e421e-128">Pokud `expression1` nebo `expression2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nula.</span><span class="sxs-lookup"><span data-stu-id="e421e-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="e421e-129">Pokus o dělení nulou</span><span class="sxs-lookup"><span data-stu-id="e421e-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="e421e-130">Pokud `expression2` vyhodnotí na hodnotu nula, `/` operátor pracuje odlišně pro různé operand datové typy.</span><span class="sxs-lookup"><span data-stu-id="e421e-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="e421e-131">V následující tabulce jsou uvedeny možné chování.</span><span class="sxs-lookup"><span data-stu-id="e421e-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="e421e-132">Operand datové typy</span><span class="sxs-lookup"><span data-stu-id="e421e-132">Operand data types</span></span>|<span data-ttu-id="e421e-133">Chování Pokud `expression2` je nulová.</span><span class="sxs-lookup"><span data-stu-id="e421e-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="e421e-134">S plovoucí desetinnou čárkou (`Single` nebo `Double`)</span><span class="sxs-lookup"><span data-stu-id="e421e-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="e421e-135">Vrátí infinity (<xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>), nebo <xref:System.Double.NaN> (není číslo) Pokud `expression1` je také nula.</span><span class="sxs-lookup"><span data-stu-id="e421e-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="e421e-136">Vyvolá<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="e421e-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="e421e-137">Integrální (podepsané nebo bez znaménka)</span><span class="sxs-lookup"><span data-stu-id="e421e-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="e421e-138">Pokus o převod zpátky do integrální typ vyvolává <xref:System.OverflowException> protože celočíselných typů nelze přijmout <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, nebo<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="e421e-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e421e-139">`/` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="e421e-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e421e-140">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="e421e-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e421e-141">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e421e-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e421e-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="e421e-142">Example</span></span>  
 <span data-ttu-id="e421e-143">Tento příklad používá `/` operátor provést s plovoucí desetinnou čárkou dělení.</span><span class="sxs-lookup"><span data-stu-id="e421e-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="e421e-144">Výsledkem je podíl dva operandy.</span><span class="sxs-lookup"><span data-stu-id="e421e-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 <span data-ttu-id="e421e-145">Výrazy v předchozím příkladu návratové hodnoty 2.5 a 3.333333.</span><span class="sxs-lookup"><span data-stu-id="e421e-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="e421e-146">Všimněte si, že výsledkem je vždy s plovoucí desetinnou čárkou (`Double`), i když jsou oba operandy konstanty typu integer.</span><span class="sxs-lookup"><span data-stu-id="e421e-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e421e-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="e421e-147">See Also</span></span>  
 [<span data-ttu-id="e421e-148">/ = – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e421e-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="e421e-149">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e421e-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="e421e-150">Datové typy výsledků operátoru</span><span class="sxs-lookup"><span data-stu-id="e421e-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [<span data-ttu-id="e421e-151">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="e421e-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="e421e-152">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e421e-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e421e-153">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="e421e-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e421e-154">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e421e-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
