---
title: '\ – operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 276071fef3632d1a617f177b6fe18026b290103a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917242"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3643c-102">\ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3643c-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="3643c-103">Vydělí dvě čísla a vrátí celočíselný výsledek.</span><span class="sxs-lookup"><span data-stu-id="3643c-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3643c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3643c-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="3643c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3643c-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="3643c-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3643c-106">Required.</span></span> <span data-ttu-id="3643c-107">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="3643c-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="3643c-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3643c-108">Required.</span></span> <span data-ttu-id="3643c-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="3643c-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="3643c-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="3643c-110">Supported Types</span></span>  
 <span data-ttu-id="3643c-111">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="3643c-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="3643c-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3643c-112">Result</span></span>  
 <span data-ttu-id="3643c-113">Výsledkem je celočíselný podíl `expression1` dělený pomocí `expression2`, který zahodí všechny zbývající a uchová pouze celočíselnou část.</span><span class="sxs-lookup"><span data-stu-id="3643c-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="3643c-114">Toto se říká *zkrácení*.</span><span class="sxs-lookup"><span data-stu-id="3643c-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="3643c-115">Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a. `expression2`</span><span class="sxs-lookup"><span data-stu-id="3643c-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="3643c-116">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="3643c-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="3643c-117">[Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplný podíl, který zachová zbytek ve zlomkové části.</span><span class="sxs-lookup"><span data-stu-id="3643c-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3643c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3643c-118">Remarks</span></span>  
 <span data-ttu-id="3643c-119">Před provedením dělení Visual Basic pokusy o převod libovolného číselného výrazu s plovoucí desetinnou čárkou na `Long`.</span><span class="sxs-lookup"><span data-stu-id="3643c-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="3643c-120">V takovém případě `Option Strict` dojde k chybě kompilátoru. `On`</span><span class="sxs-lookup"><span data-stu-id="3643c-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="3643c-121">Pokud `Option Strict` <xref:System.OverflowException> je `Off`, je možné, že je hodnota mimo rozsah [dlouhého datového typu](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="3643c-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="3643c-122">Převod na `Long` je také předmětem *zaokrouhlování bank*.</span><span class="sxs-lookup"><span data-stu-id="3643c-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="3643c-123">Další informace naleznete v části "zlomkové části" v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3643c-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="3643c-124">Pokud `expression1` je `expression2` nebo se vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude se zacházet jako nula.</span><span class="sxs-lookup"><span data-stu-id="3643c-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="3643c-125">Došlo k pokusu o dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="3643c-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="3643c-126">Pokud `expression2` je hodnota vyhodnocena jako `\` nula, operátor <xref:System.DivideByZeroException> vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="3643c-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="3643c-127">To platí pro všechny číselné datové typy operandů.</span><span class="sxs-lookup"><span data-stu-id="3643c-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3643c-128">Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `\`</span><span class="sxs-lookup"><span data-stu-id="3643c-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3643c-129">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="3643c-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3643c-130">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3643c-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3643c-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="3643c-131">Example</span></span>  
 <span data-ttu-id="3643c-132">Následující příklad používá `\` operátor k provedení dělení celého čísla.</span><span class="sxs-lookup"><span data-stu-id="3643c-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="3643c-133">Výsledkem je celé číslo, které představuje celočíselný podíl dvou operandů a zbytek byl zahozen.</span><span class="sxs-lookup"><span data-stu-id="3643c-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="3643c-134">Výrazy v předchozím příkladu vrací hodnoty 2, 3, 33 a-22 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3643c-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3643c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3643c-135">See also</span></span>

- [<span data-ttu-id="3643c-136">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="3643c-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="3643c-137">/– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3643c-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="3643c-138">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="3643c-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="3643c-139">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="3643c-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="3643c-140">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3643c-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3643c-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="3643c-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3643c-142">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3643c-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
